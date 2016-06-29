<template>
  <navbar></navbar>
  <div class="g-c f-cb">
    <tree></tree>
    <list></list>
  </div>
</template>

<script>
  import Navbar from './Navbar.vue'
  import Tree from './Tree.vue'
  import List from './List.vue'

  export default {
    components: {
      Tree,
      List,
      Navbar
    },
    route:  {
        canReuse:function(){
          //不可以复用
          return false;
        }
    }
  }
</script>

<style>

</style>
