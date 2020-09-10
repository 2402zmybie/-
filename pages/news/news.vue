<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true"  @clickRight="openAdd">
			<!-- 左边插槽 -->
			<block slot="left">
				<view class="nav-left">
					<view class="icon iconfont icon-qiandao"></view>
				</view>
			</block>
			<!-- 中间插槽 -->
			<view class="nav-tab-bar u-f-ajc">
				<block v-for="(item,index) in tabBars" :key="item.id">
					<view class="active u-f-ajc" :class="{'active': tabIndex == index}" @tap="changeTap(index)">
						{{ item.name }} 
						<view v-if="tabIndex == index" class="nav-tab-bar-line"></view> 
					</view>
				</block>
				
			</view>
			<!-- 右边插槽 -->
			<block slot="right">
				<view class="nav-right u-f-ajc">
					<view class="icon iconfont icon-bianji1"></view>
				</view>
			</block>
		</uni-nav-bar>
		<!-- 列表 -->
		<view class="common-list u-f">
			<view class="common-list-l">
				<image src="../../static/demo/userpic/19.jpg" mode="widthFix" lazy-load></image>
			</view>
			<view class="common-list-r">
				<view class="u-f-ac u-f-jsb">
					<view class="u-f-ac">老何<view class="icon iconfont icon-nan tag-sex">25</view></view>
					<view class="icon iconfont icon-zengjia">关注</view>
				</view>
				<view>我是标题</view>
				<view class="u-f-ajc">
					<!-- 图片 -->
					<image src="../../static/demo/datapic/17.jpg" mode="widthFix" lazy-load></image>
					<!-- 视频 -->
					<view class="common-list-play icon iconfont icon-bofang"></view>
					<view class="common-list-playinfo">
						20w次播放 2:47
					</view>
				</view>
				<view class="u-f-ac u-f-jsb">
					<view>深圳 龙岗</view>
					<view class="u-f-ac">
						<view class="icon iconfont icon-zhuanfa">10</view>
						<view class="icon iconfont icon-pinglun1">20</view>
						<view class="icon iconfont icon-dianzan1">998</view>
					</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	export default {
		comments:{
			uniNavBar
		},
		data() {
			return {
				tabIndex:0,
				tabBars:[
					{
						name:"关注",
						id:"guanzhu"
					},
					{
						name:"话题",
						id:"topic"
					}
				]
			}
		},
		methods: {
			changeTap(index) {
				this.tabIndex = index;
			},
			openAdd() {
				uni.navigateTo({
					url:"../add-input/add-input"
				})
			}
		}
	}
</script>

<style lang="scss">
.nav-right>view,.nav-left>view{
		font-size: 40upx;
	}
	.nav-left>view{
		color: #FF9619;
	}
	
	.nav-left{
		margin-left: 16upx;
	}
	.nav-right{
		width: 100%;
	}
	.nav-tab-bar{
		width: 100%;
		margin-left: -20upx;
		position: relative;
	}
	.nav-tab-bar>view{
		font-size: 35upx;
		padding: 0 15upx;
		font-weight: bold;
		color: #969696;
	}
	.active{
		color: #333333 !important;
	}
	.nav-tab-bar-line{
		position: absolute;
		bottom: 0upx;
		border-bottom: 5upx solid #FEDE33;
		border-top: 5upx solid #FEDE33;
		width: 70upx;
		border-radius: 20upx;
	}
	
	/* #ifdef MP-WEIXIN */
		.uni-status-bar{
			height: 0!important;
		}
	/* #endif */
	
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
.tag-sex  {
	background: #007AFF;
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
		font-size: 100upx;
		
	}
	.common-list-playinfo {
		position: absolute;
		bottom: 0;
		right: 10upx;
		background: #333333;
		border-radius: 20upx;
		padding: 0 15upx;
		color: #FFFFFF;
	}
}
.common-list-r>view:nth-child(4)>view {
	color: #AAAAAA;
}
.common-list-r>view:nth-child(4)>view:last-child>view {
	margin-left: 10upx;
	padding-left: 5upx;
}
</style>
