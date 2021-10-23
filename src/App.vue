<template>
  <ul id="demo">
    <tree-item
      class="item"
      :item="treeData"
      @make-folder="makeFolder"
    ></tree-item>
  </ul>
</template>

<script>
import treeItem from './components/TreeItem.vue'
import data from '../public/static/node_modules.json'

const treeData = data
export default {
  name: 'demo',

  data: function() {
    return {
      treeData: treeData,
    }
  },
  components: {
    treeItem,
  },
  methods: {
    makeFolder: function(item) {
      this.set(item, 'contents', [])
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
body {
  font-family: Menlo, Consolas, monospace;
  color: #444;
}
.container {
  width: 800px;
  margin: 0 auto;

  margin-top: 100px;
}
.item {
  cursor: pointer;
}
.item_name {
  color: rgb(19, 131, 146);
}
.bold {
  font-weight: bold;
}
ul {
  padding-left: 1em;
  line-height: 1.5em;
  list-style-type: dot;
}
ul > li::marker {
  font-weight: bold;
}
</style>
