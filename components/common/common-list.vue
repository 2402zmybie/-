<template>
	<view class="common-list u-f  animated fadeInLeft fast">
		<view class="common-list-l">
			<image :src="item.userpic" mode="widthFix" lazy-load></image>
		</view>
		<view class="common-list-r">
			<view class="u-f-ac u-f-jsb">
				<view class="u-f-ac">{{ item.username }}<view class="icon iconfont" :class="[item.sex == 0?'icon-nan tag-sex-nan':'icon-nv tag-sex-nv']">{{ item.age }}</view></view>
				<view class="icon iconfont icon-zengjia" v-if="!isguanzhu" @tap="guanzhu">关注</view>
			</view>
			<view>{{ item.title }}</view>
			<view class="u-f-ajc">
				<!-- 图片 -->
				<image v-if="item.titlepic" :src="item.titlepic" mode="widthFix" lazy-load></image>
				<!-- 视频 -->
				<template v-if="item.video">
					<view class="common-list-play icon iconfont icon-bofang"></view>
					<view class="common-list-playinfo">
						{{ item.video.looknum }}次播放 {{ item.video.long }}
					</view>
				</template>
				
				<!-- 分享 -->
				<view v-if="item.share" class="common-list-share u-f-ac">
					<image class="common-list-share-image" :src="item.share.titlepic" mode="widthFix" lazy-load></image>
					<view>{{ item.share.title }}</view>
				</view>
			</view>
			<view class="u-f-ac u-f-jsb">
				<view>{{ item.path }}</view>
				<view class="u-f-ac">
					<view class="icon iconfont icon-zhuanfa">{{ item.sharenum }}</view>
					<view class="icon iconfont icon-pinglun1">{{ item.commentnum }}</view>
					<view class="icon iconfont icon-dianzan1">{{ item.goodnum }}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			item:Object,
			index:Number
		},
		data() {
			return {
				isguanzhu: this.item.isguanzhu
			}
		},
		methods: {
			guanzhu() {
				this.isguanzhu = true;
				uni.showToast({
					title: '关注成功'
				});
			}
		}
	}
</script>

<style lang="scss" scoped>
// 列表
.common-list {
	padding: 20upx;
}
.common-list-l {
	flex-shrink: 0;
	image{
		width: 90upx;
		height: 90upx;
		border-radius: 100%;
	}
}

.common-list-r {
	flex: 1;
	margin-left: 15upx;
	border-bottom: 1upx solid #EEEEEE;
	padding-bottom: 10upx;
}

.common-list-r>view:nth-child(1)>view:first-child {
	color: #999999;
	font-size: 32upx;
}
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
.common-list-r>view:nth-child(1)>view:last-child {
	background: #EEEEEE;
	padding: 0 10upx;
	font-size: 26upx;
}
.common-list-r>view:nth-child(2) {
	font-size: 32upx;
	margin: 15upx 0;
}
.common-list-r>view:nth-child(3) {
	position: relative;
	image {
		width: 100%;
		border-radius: 10upx;
	}
	.common-list-play {
		position: absolute;
		color: #FFFFFF;
		font-size: 130upx;
		
	}
	.common-list-playinfo {
		position: absolute;
		bottom: 0;
		right: 10upx;
		background: rgba(51,51,51,0.73);
		border-radius: 20upx;
		padding: 0 20upx;
		color: #FFFFFF;
		font-size: 26upx;
	}
}
.common-list-r>view:nth-child(4)>view {
	margin-top: 10upx;
	color: #AAAAAA;
}
.common-list-r>view:nth-child(4)>view:last-child>view {
	margin-left: 10upx;
	padding-left: 5upx;
	font-size: 28upx;
}
.common-list-share{
	background: #EEEEEE;
	width: 100%;
	border-radius:10upx ;
	padding: 10upx;
}
.common-list-share image{
	width: 200upx;
	height: 150upx;
	margin-right: 10upx;
}
</style>
