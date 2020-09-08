<template>
	<view>
		监听属性: 在封装组件中使用较多,监听某一个属性,通知父组件改变
		<view class="font"> {{ num }}</view>
		<view v-if="num > 10">优秀</view>
		<button type="primary" @tap="change">修改</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num:0
			}
		},
		watch:{
			num(val) {
				console.log("num被修改了:" + val)
			}
		},
		methods: {
			change() {
				this.num++
			}
		}
	}
</script>

<style>
.font {
	font-size: 30upx;
	color: #000000;
}
</style>
