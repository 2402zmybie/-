<template>
	<view class="icon iconfont" :class="[sex == 0?'icon-nan tag-sex-nan':'icon-nv tag-sex-nv']">{{ age }}</view>
</template>

<script>
	export default {
		props:{
			sex:Number,
			age:Number
		}
	}
</script>

<style>
.tag-sex-nan  {
	background: #007AFF;
	color: #FFFFFF;
	font-size: 23upx;
	padding: 5upx 10upx;
	margin-left: 10upx;
	border-radius: 20upx;
	line-height: 22upx;
}
.tag-sex-nv  {
	background: pink;
	color: #FFFFFF;
	font-size: 23upx;
	padding: 5upx 10upx;
	margin-left: 10upx;
	border-radius: 20upx;
	line-height: 22upx;
}
</style>
