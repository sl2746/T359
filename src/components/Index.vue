<template>
	<div class="s-homepage-bg">
		<div class="s-homepage-content">
		  	<div class="s-homepage-logo">
			  	<div class="s-homepage-fun">
			  		<a>新闻</a>
			  		<a>热点</a>
			  		<a>实务</a>
			  		<a>|</a>
			  		<a>登录</a>
			  		<a>注册</a>
			  	</div>
		  	</div>
		  	<div id="guideDiv" class="s-homepage-guide">
		  		<table>
		  			<tr>
		  				<td width="260px"><a class="s-homepage-btn-1" v-link="{path: '/main/sources',query: {nm: '基础法律'}}"><!-- 基础法律 --></a></td>
		  				<td width="160px"><a class="s-homepage-btn-2" v-link="{path: '/main/sources',query: {nm: '食品法律'}}"><!-- 食品法律 --></a></td>
		  				<td width="180px"><a class="s-homepage-btn-3" v-link="{path: '/main/sources',query: {nm: '药品法律'}}"><!-- 药品法律 --></a></td>
		  				<td width="220px"><a class="s-homepage-btn-4" v-link="{path: '/main/sources',query: {nm: '医疗器械法律'}}"><!-- 医疗器械法律 --></a></td>
		  				<td width="180px"><a class="s-homepage-btn-5" v-link="{path: '/main/sources',query: {nm: '医事法律'}}"><!-- 医事法律 --></a></td>
		  			</tr>
		  		</table>
		  	</div>
	  		<div class="s-homepage-copyright">@Copyright 2016-2017 江湖健法</div>
	  	</div>
	</div>
</template>

<script>
  export default {
  }
</script>

<style>
	@import '../css/homepage.css';
</style>
