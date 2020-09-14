<template>
	<view class="paper-list u-f-ac animated fadeInLeft fast">
		<image :src="item.userpic" mode="widthFix" lazy-load></image>
		<view>
			<view class="u-f-ac u-f-jsb">
				{{ item.username }}
				<view>{{ item.time }}</view>
			</view>
			<view class="u-f-ac u-f-jsb">
				{{ item.data }}
				<template v-if="item.noreadnum != 0">
					<uni-badge :text="item.noreadnum + ''" type="error"></uni-badge>
				</template>
			</view>
		</view>
	</view>
</template>

<script>
	import uniBadge from '../../components/uni-badge/uni-badge.vue'
	export default {
		components: {
			uniBadge
		},
		props: {
			item:Object
		}
	}
</script>

<style lang="scss">
.paper-list {
	border-bottom: 1upx solid #EEEEEE;
	padding: 20upx 0;
	image {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		margin-right: 20upx;
		flex-shrink: 0;
	}
	>view {
		flex: 1;
		>view:nth-child(1) {
			font-size: 35upx;
			>view {
			   color: #CBCBCB;
			}
		}
		>view:nth-child(2) {
			color: #999999;
		}
	}
}
</style>
