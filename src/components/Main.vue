<template>
	<div class="s-index-bg">
		<div class="g-c">
    		<v-header></v-header>
    		<router-view></router-view>
		</div>
	</div>
</template>

<script>
  import Header from './../components/Header.vue';
  import Container from './../components/Container.vue';
  import PubSub from "pubsub-js";
  import Vue from 'vue'
	
	var cc = new Vue({
		data:{
			subname:''
		}
	})
  
  var comdata = {}
  
  // 全局注册组件
  Vue.component('sl-subtitle', {
    props: ['subname'],
    template: '{{subname}}'
  })


  export default {
    components: {
      vHeader: Header,
      vContainer: Container
    },
    ready:function(){
    	cc.subname = this.$route.query.nm
    	comdata.nm = this.$route.query.nm
    	
      this.$http.get(`http://61.139.87.61:8880/effectLevels`)
      .then(response => {
        PubSub.publish('effectLevels', {
          effectLevels: response.data
        });
      });
    }
  }
</script>

<style>
  @import '../css/lib/reset.css';
  @import '../css/lib/function.css';
  @import '../css/index.css';
</style>
