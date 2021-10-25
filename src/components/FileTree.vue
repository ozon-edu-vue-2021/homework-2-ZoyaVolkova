<template>
  <ol id="file-tree">
    <tree-item class="item" :item="treeData"></tree-item>
  </ol>
</template>

<script>
import treeItem from './TreeItem.vue'
import treeData from '../../public/static/node_modules.json'

export default {
  name: 'file-tree',
  data: function() {
    return {
      treeData: treeData,
    }
  },
  components: {
    treeItem,
  },
}
</script>

<style>
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
  font-size: 30px;
}
.container {
  width: 1600px;
  margin-left: 150px;
  margin-top: 100px;
}

#file-tree,
.list {
  padding-left: 1em;
  line-height: 1.5em;
}
</style>
