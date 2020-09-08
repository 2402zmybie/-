<template>
	<view class="content">
		<view class="index-list">
			<view class="index-list1">
				<view class="index-list1-left">
					<image src="../../static/demo/userpic/12.jpg" mode="widthFix" lazy-load></image>昵称
				</view>
				<view class="index-list1-right">
					<view class="icon iconfont icon-zengjia"></view>关注
				</view>
			</view>
			<view class="index-list2">我是标题</view>
			<view class="index-list3">
				<image src="../../static/demo/datapic/11.jpg" mode="widthFix" lazy-load></image>
				<!-- 视频播放按钮 -->
				<view class="icon iconfont icon-bofang index-list-play"></view>
				<!-- 右下角视频播放信息 -->
				<view class="index-list-playinfo">
					20w次播放 2:47
				</view>
			</view>
			<view class="index-list4">
				<!-- 左边顶和踩 -->
				<view class="index-list4-left">
					<view>
						<view class="icon iconfont icon-icon_xiaolian-mian index-list4-image"></view>10
					</view>
					<view>
						<view class="icon iconfont icon-kulian index-list4-image"></view>5
					</view>
				</view>
				<!-- 右边评论转发等 -->
				<view class="index-list4-right">
					<view>
						<view class="icon iconfont icon-pinglun1 index-list4-image"></view>40 
					</view>
					<view>
						<view class="icon iconfont icon-zhuanfa index-list4-image"></view>50 
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style scoped lang="scss">
.index-list {
	padding: 20upx;
	border-bottom: 1px solid #BEBEBE;
}
.index-list1 {
	display: flex;
	justify-content: space-between;
	align-items: center;
	// 头像
	.index-list1-left {
		display: flex;
		align-items: center;
		image {
			width: 90upx;
			height: 90upx;
			margin-right: 16upx;
			border-radius: 50%;
		}
	}
	.index-list1-right {
		display: flex;
		align-items: center;
		background: #EEEEEE;
		padding: 0 10upx;
	}
	
}
.index-list2 {
	margin: 20upx 0;
	color: #000000;
	font-size: 30upx;
}
.index-list3 {
	position: relative;
	display: flex;
	justify-content: center;
	align-items: center;
	image {
		width: 100%;
		border-radius: 10upx;
	}
	.index-list-play {
		position: absolute;
		font-size: 140upx;
		color: #FFFFFF;
	}
	.index-list-playinfo {
		position: absolute;
		background: rgba(51,51,51,0.72);
		color: #FFFFFF;
		font-size: 22upx;
		right: 8upx;
		bottom: 8upx;
		padding: 0 10upx;
		border-radius: 40upx;
	}
}
.index-list4 {
	display: flex;
	justify-content: space-between;
	align-items: center;
	color: #BEBEBE;
	.index-list4-image {
		margin-right: 8upx;
	}
	.index-list4-left {
		display: flex;
		view{
			display: flex;
			align-items: center;
			:last-child{
				margin-left: 10upx;
			}
		}
		
	}
	.index-list4-right {
		display: flex;
		view{
			display: flex;
				align-items: center;
				:last-child{
					margin-left: 10upx;
				}
		}
		
	}
}
</style>
