<template>
  <no-ssr>
    <div class="container">
      <div>
        <TreeItem
          class="item"
          :item="treeData"
          @make-folder="makeFolder"
          @add-item="addItem"
        />
      </div>
    </div>
  </no-ssr>
</template>

<script>
import TreeItem from '~/components/TreeItem.vue'
import treeData from '~/lib/treeData.js'

export default {
  components: {
    TreeItem
  },
  data () {
    return { treeData: treeData }
  },
  methods: {
  	makeFolder: function (item) {
    	this.$set(item, 'children', [])
      this.addItem(item)
    },
    addItem: function (item) {
    	item.children.push({
        name: 'new stuff'
      })
    }
  }
}
</script>

<style>
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
</style>
