<template>
	<uni-nav-bar  :statusBar="true"  @clickRight="openAdd" :border="false">
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
</template>

<script>
	export default {
		props:{
			tabBars:Array,
			tabIndex:Number
		},
		methods:{
			//向父组件通信
			changeTap(index) {
				this.$emit('change-tab',index)
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
			/* .uni-status-bar{
				height: 0!important;
			} */
		/* #endif */
</style>
