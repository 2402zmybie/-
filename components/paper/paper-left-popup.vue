<template>
	<view>
		<!-- 操作菜单 -->
		<view class="paper-left-popup-mask" v-show="show" @tap="hidepopup"></view>
		<view class="paper-left-popup" v-show="show">
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="addfriend">
				<view class="icon iconfont icon-sousuo"></view>
				加糗友
			</view>
			<view style="height: 1px; background: #CCCCCC;"></view>
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="clear">
				<view class="icon iconfont icon-qingchu"></view>
				清除缓存
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props:{
			show:Boolean
		},
		methods:{
			hidepopup() {
				this.$emit("hidepopup")
			},
			addfriend() {
				this.$emit("addfriend")
			},
			clear() {
				this.$emit("clear")
			}
		}
	}
</script>

<style lang="scss">
.paper-left-popup-mask {
	position: fixed;
	right: 0;
	left: 0;
	top: 0;
	bottom: 0;
	z-index: 1999;
	
}
.paper-left-popup {
	position: fixed;
	right: 0;
	top: 10upx;
	background: #FFFFFF;
	z-index: 2000;
	width: 55%;
	box-shadow: 1upx 1upx 20upx #CCCCCC;
	>view:nth-child(1), view:nth-child(3){
		padding: 20upx;
		font-size: 35upx;
		>view {
			margin-right: 10upx;
			font-weight: bold;
		}
	}
}
.paper-left-popup-h {
	background: #EEEEEE;
}
</style>
