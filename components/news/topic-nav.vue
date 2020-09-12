<template>
	<view class="topic-nav">
		<view class="u-f-ac u-f-jsb">
			<view>热门分类</view>
			<view class="u-f-ac">
				更多<view class="icon iconfont icon-jinru"></view>
			</view>
		</view>
		<view class="u-f-ac">
			<block v-for="(item,index) in navs" :key="index">
				<view class="u-f-ajc">{{ item.name }}</view>
			</block>
		
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			navs:Array
		}
	}
</script>

<style lang="scss">
// 热门分类 注意scss的写法
.topic-nav {
	border-bottom: 1upx solid #EEEEEE;
	border-top: 1upx solid #EEEEEE;
	padding: 20upx;
	>view:nth-child(1){
		margin-bottom: 10upx;
		>view:nth-child(1) {
			color: #333333;
			font-size: 32upx;
		}
		>view:nth-child(2) {
			color: #9E9E9E;
		}
	}
	>view:nth-child(2) {
		view{
			flex: 1;
			background: #EEEEEE;
			color: #9E9E9E;
			border-radius: 10upx;
			margin: 0 10upx;
		}
	}
}
</style>
