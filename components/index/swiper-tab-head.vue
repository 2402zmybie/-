<template>
	<view class="uni-tab-bar">
		<scroll-view class="uni-swiper-tab" scroll-x :style="scrollStyle">
			<block v-for="(tab,index) in tabBars" :key="tab.id" :style="scrollStyle">
				<view 
					class="swiper-tab-list" 
					:class="{'active' : tabIndex==index}"
					@tap="tabtap(index)"
					:style="scrollItemStyle"
					>
					{{tab.name}} {{tab.num?tab.num:""}}
					<view class="swiper-tab-line" ></view>
				</view>
			</block>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		props:{
			tabBars: Array,
			tabIndex: Number,
			scrollStyle:{
				type:String,
				default: ""
			},
			scrollItemStyle: {
				type:String,
				default:""
			}
		},
		methods:{
			//tab点击事件, 子组件向父组件传值
			tabtap(index) {
				this.$emit("tabtap",index)
			},
		}
	}
</script>

<style lang="scss">
.uni-swiper-tab {
	border-bottom: 1upx solid #EEEEEE;
	.active {
		color: #343434;
		.swiper-tab-line {
			border-bottom: 6upx solid #FEDE33;
			width: 70upx;
			margin: auto;
			border-top: 6upx solid #FEDE33;
			border-radius: 20upx;
		}
	}
}
.swiper-tab-list{
	color: #969696;
	font-weight: bold;
}
</style>
