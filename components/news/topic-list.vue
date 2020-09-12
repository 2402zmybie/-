<template>
	<view class="topic-list u-f">
		<image :src="item.titlepic" mode="widthFix" lazy-load></image>
		<view>
			<view>#{{ item.title }}#</view>
			<view>{{ item.desc }}</view>
			<view>动态{{ item.totalnum }} 今日 {{ item.todaynum }}</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object
		}
	}
</script>

<style lang="scss">
.topic-list {
		padding: 20upx 0;
		border-bottom: 1upx solid #EEEEEE;
		image {
			width: 150upx;
			height: 150upx;
			border-radius: 10upx;
			margin-right: 20upx;
		}
		>view {
			color: #A4A4A4;
			>view:nth-child(1) {
				color: #333333;
				font-size: 32upx;
			}
		}
	}
</style>
