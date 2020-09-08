<template>
	<view class="index-list">
		<view class="index-list1">
			<view class="index-list1-left">
				<image :src="item.userpic" mode="widthFix" lazy-load></image>{{ item.username }}
			</view>
			<view class="index-list1-right" v-show="item.isguanzhu">
				<view class="icon iconfont icon-zengjia"></view>关注
			</view>
		</view>
		<view class="index-list2">{{ item.title }}</view>
		<view class="index-list3" >
			<image :src="item.titlepic" mode="widthFix" lazy-load></image>
			<template v-if="item.type === 'video'">
				<!-- 视频播放按钮 -->
				<view class="icon iconfont icon-bofang index-list-play"></view>
				<!-- 右下角视频播放信息 -->
				<view class="index-list-playinfo">
					{{ item.playnum }}次播放 {{ item.long }}
				</view>
			</template>
		</view>
		<view class="index-list4">
			<!-- 左边顶和踩 -->
			<view class="index-list4-left">
				<view :class="{'active': (item.infonum.index == 1)}">
					<view class="icon iconfont icon-icon_xiaolian-mian index-list4-image"></view>{{ item.infonum.dingnum }}
				</view>
				<view :class="{'active': (item.infonum.index == 2)}">
					<view class="icon iconfont icon-kulian index-list4-image"></view>{{ item.infonum.cainum }}
				</view>
			</view>
			<!-- 右边评论转发等 -->
			<view class="index-list4-right">
				<view>
					<view class="icon iconfont icon-pinglun1 index-list4-image"></view>{{ item.commentnum }}
				</view>
				<view>
					<view class="icon iconfont icon-zhuanfa index-list4-image"></view>{{ item.sharenum }}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:['item','index'],
		data() {
			return {
				
			};
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
	.active {
		color: #FFFF00;
	}
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
