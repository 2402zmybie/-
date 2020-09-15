<template>
	<view class="user-list u-f-ac animated fadeInLeft fast">
		<image :src="item.userpic" mode="widthFix" lazy-load></image>
		<view>
			<view>
				{{ item.username }}
			</view>
			<view style="display: inline-block;">
				<tag-sex-age :age="item.age" :sex="item.sex"></tag-sex-age>
			</view>
		</view>
		<template v-if="!item.isguanzhu">
			<view class="icon iconfont icon-zengjia1 u-f-ajc" ></view>
		</template>
		<template v-else>
			<view class="icon iconfont icon-xuanze-yixuan u-f-ajc"></view>
		</template>
	</view>
</template>

<script>
	import tagSexAge from '../../components/common/tag-sex-age.vue'
	export default {
		components:{
			tagSexAge
		},
		props:{
			item:Object
		}
	}
</script>

<style lang="scss">
.user-list {
	padding: 20upx 0;
	margin: 0 20upx;
	border-bottom: 1upx solid #EEEEEE;
	image {
		width: 120upx;
		height: 120upx;
		flex-shrink: 0;
		border-radius: 50%;
	}
	>view:first-of-type {
		flex: 1;
		>view:first-child{
			font-size: 35upx;
			
		}
	}
	>view:last-of-type{
		width: 80upx;
		color: #CCCCCC;
	}
}

.icon-zengjia1 {
	color: #F8791B !important;
}
</style>
