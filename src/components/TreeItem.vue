<template>
  <li>
    <div
      tabindex="0"
      :class="[{ bold: isDirectory }, { item_name: !isDirectory }]"
      @click="toggle"
    >
      <img v-if="isDirectory" src="../assets/folder.png" />
      <img v-if="isFile" src="../assets/file.png" />
      <img v-if="isLink" src="../assets/link.png" />
      {{ item.name }}
      <span v-if="isDirectory">[{{ isOpen ? '-' : '+' }}]</span>
    </div>
    <ol v-show="isOpen" v-if="isDirectory" :class="item.name">
      <tree-item
        class="item"
        v-for="(child, index) in item.contents"
        :key="index"
        :item="child"
      ></tree-item>
    </ol>
  </li>
</template>

<script>
export default {
  name: 'tree-item',
  props: {
    item: Object,
  },
  data: function() {
    return {
      isOpen: false,
    }
  },
  computed: {
    isDirectory: function() {
      return this.item.contents && this.item.contents.length
    },
    isFile: function() {
      return this.item.type === 'file'
    },
    isLink: function() {
      return this.item.type === 'link'
    },
  },
  methods: {
    toggle: function() {
      if (this.isDirectory) {
        this.isOpen = !this.isOpen
      }
    },
  },
}
</script>
