<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @clickLeft="back" @clickRight="submit">
			<view class="title-slot" @tap="changelook">
				{{ yinsi }}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar";
	let changelook = ['所有人可见', '仅自己可见'];
	export default {
		components: {
			uniNavBar
		},
		data() {
			return {
				yinsi: "所有人可见"
			}
		},
		methods: {
			back() {
				console.log(111)
				uni.navigateBack({
					delta: 1
				});
			},
			changelook() {
				uni.showActionSheet({
				    itemList: changelook,
				    success: (res) => {
				       this.yinsi = changelook[res.tapIndex]
				    },
				});
			},
			submit() {
				console.log("发布")
			}
		}
	}
</script>

<style lang="scss">
.title-slot {
	display: flex;
	justify-content: center;
	align-items: center;
}
</style>
