<template>
	<view class="user-chat-bottom u-f-ac">
		<input type="text" placeholder="文明发言" v-model="text"/>
		<view class="icon iconfont icon-fabu u-f-ajc" @tap="submit"></view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text: ""
			}
		},
		methods:{
			submit() {
				this.$emit("submit",this.text)
				this.text = ""
			}
		}
	}
</script>

<style lang="scss" scoped>
.user-chat-bottom {
	position: fixed;
	left: 0;
	bottom: 0;
	right: 0;
	height: 120upx;
	// 上右下左,  上下是0左右是20upx
	padding: 0 20upx;
	background: #FFFFFF;
	border-top: 1upx solid #EEEEEE;
	input {
		flex: 1;
		margin-right: 20upx;
		padding: 10upx;
		border-radius: 10upx;
		background: #FFFFFF;
	}
	view {
		width: 80upx;
		font-size: 45upx;
		
	}
}
</style>
