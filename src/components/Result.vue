<template>
  <div class="m-search-result">
    <h1>关键词：<span class="keyword" v-text="$route.query.keyword"></span></h1>
    <ul class="result-list">
      <resultitem :model="searchData"></resultitem>
    </ul>
  </div>
</template>

<script>
  import Vue from 'vue';

  let strVar='';
  strVar += '<li v-for=\"item in model.items\">'
  strVar += '<i class="u-icon u-icon-24 u-icon-question"></i>'
  strVar += '<a href="###">{{item.name}}</a>'
  strVar += '</li>';

  // item 组件，用于实现查询结果
  Vue.component('resultitem', {
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
        }
      },
      changeType: function () {
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
        searchData: {}
      }
    },
    route: {
      data: function (transition) {
        this.$http.get(`http://61.139.87.61:8880/conditions?keyword=${this.$route.query.keyword}`)
        .then(response => {
          this.searchData = response.data
        });
      }
    }
  }
</script>

<style>
  @import '../css/result.css';
</style>
