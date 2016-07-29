<template>
  <header class="g-h">
   	<div class="s-logo-main">
    <a href="###" class="s-login">注册</a>
    <a href="###" class="s-login">登录</a>
    </div>
  </header>
  <div class="f-cb">
    <breadcrumb></breadcrumb>
    <search></search>
  </div>
</template>

<script>
  import Breadcrumb from './Breadcrumb.vue'
  import Search from './Search.vue'

  export default {
    components: {
      Breadcrumb,
      Search
    }
  }
</script>

<style>
  @import '../css/header.css';
  @import '../css/common.css';
</style>
