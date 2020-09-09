<template>
	<!-- 上拉加载更多 -->
	<view class="load-more">{{ loadtext }}</view>
</template>

<script>
	export default {
		props:{
			loadtext:String
		}
	}
</script>

<style>
.load-more {
	text-align: center;
	color: #AAAAAA;
	padding: 10upx;
}
</style>
