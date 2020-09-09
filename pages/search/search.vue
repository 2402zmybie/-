<template>
	<view>
		搜索也
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		//监听原生标题导航按钮点击事件. 参数为Object, 要转化为String
		onNavigationBarButtonTap(e) {
			console.log(JSON.stringify(e))
			if(e.index == 0) {
				//点击第一个按钮
				uni.navigateBack({
					//返回上一页
					delta: 1
				});
			}
			
		},
		//监听原生标题栏搜索输入框输入内容变化事件
		onNavigationBarSearchInputChanged(e) {
			console.log("输入" + JSON.stringify(e))
		},
		//监听原生标题栏搜索输入框搜索事件，用户点击软键盘上的“搜索”按钮时触发。
		onNavigationBarSearchInputConfirmed(e) {
			console.log("搜索" + JSON.stringify(e))
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
