<template>
  <ul class="m-tree f-fl">
    <item class="item" :model="treeData"></item>
  </ul>
</template>

<script>
  import Vue from 'vue';
  import PubSub from "pubsub-js";

  let strVar="";
  strVar += "<li>";
  strVar += "      <div";
  strVar += "        :class=\"{bold: isFolder}\"";
  strVar += "        @click=\"toggle\"";
  strVar += "        @dblclick=\"changeType\">";
  strVar += "        <span v-if=\"isFolder\"><img v-if=\"open\"src=\"../src/img/square_remove.png\"><img v-else src=\"../src/img/square_add.png\"><\/span>";
  strVar += "        {{model.name}}";
  strVar += "      <\/div>";
  strVar += "      <ul v-show=\"open\" v-if=\"isFolder\">";
  strVar += "        <item";
  strVar += "          class=\"item\"";
  strVar += "          v-for=\"model in model.children\"";
  strVar += "          :model=\"model\">";
  strVar += "        <\/item>";
  strVar += "      <\/ul>";
  strVar += "<\/li>";

  // item 组件，用于做树形菜单
  Vue.component('item', {
    template: strVar,
    props: {
      model: Object
    },
    data: function () {
      return {
        open: false
      }
    },
    computed: {
      isFolder: function () {
        return this.model.children &&
          this.model.children.length
      }
    },
    methods: {
      toggle: function () {
        if (this.isFolder) {
          this.open = !this.open
        }else {
          PubSub.publish('category_id', {
            category_id: this.model.id
          });
        }
      },
      changeType: function () {
        console.log(!this.isFolder);
        if (!this.isFolder) {
          Vue.set(this.model, 'children', [])
          this.addChild()
          this.open = true
        }
      }
    }
  })

  export default {
    data() {
      return {
        treeData: {}
      }
    },
    ready() {
      this.$http.get(`http://61.139.87.61:8880/categories`).then(response => {
        this.treeData = response.data[2]
      })
    }
  }
</script>

<style>
  @import '../css/tree.css';
</style>
