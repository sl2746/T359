<template>
  <ul class="m-navbar">
    <li v-link="{ path: '/questions', activeClass: 'active' }"><a>问&nbsp;&nbsp;题</a></li>
    <li v-link="{ path: '/cases', activeClass: 'active' }"><a>案&nbsp;&nbsp;例</a></li>
    <li v-link="{ path: '/sources', activeClass: 'active' }"><a>法&nbsp;&nbsp;律</a></li>
    <li v-link="{ path: '/contracts', activeClass: 'active' }"><a>合&nbsp;&nbsp;同</a></li>
    <li v-link="{ path: '/literatures', activeClass: 'active' }"><a>文&nbsp;&nbsp;献</a></li>
  </ul>
</template>

<script>
  export default {
  }
</script>

<style>
  @import '../css/navbar.css';
</style>
