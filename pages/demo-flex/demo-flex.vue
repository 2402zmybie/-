<template>
	<scroll-view>
		<text>
			flex布局的使用, 用于跨端的布局:\n
			1: 如果不设置flex-wrap: wrap; 则所有的格子会挤在一行, 格子的宽度设置没用\n
			2: 设置flex-wrap: wrap; 则自动换行; flex-wrap: wrap-reverse,则反向换行\n
			3: justify-content: center;子元素横向居中显示, justify-content: space-between;两端对其 justify-content: flex-end右边对其\n
			4: align-items: center;子元素竖向居中显示
			5: 要设置盒子内的居中, 则设置
		</text>
		
		<view class="box">
			<view class="box-item">1</view>
			<view class="box-item">2</view>
			<view class="box-item">3</view>
			
		</view>
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style scoped>
.box {
	width: 100%;
	border: 1upx solid #CCCCCC;
	height: 500upx;
	display: flex;
	justify-content: flex-end;
	align-items: center;
}
.box-item {
	background: #007AFF;
	color: #FFFFFF;
	height: 200upx;
	width: 200upx;
	line-height: 200upx;
	font-size: 30upx;
	font-weight: bold;
	display: flex;
	justify-content: center;
	align-items: center;
}
/* css3选择器 */
.box-item:nth-of-type(odd){
	background: red;
}
.box-item:nth-of-type(even) {
	background: yellow;
}
</style>
