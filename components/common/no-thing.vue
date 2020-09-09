<template>
	<view class="nothing animated fadeIn">
		<image src="../../static/common/nothing.png" mode="widthFix"></image>
	</view>
</template>

<script>
	export default {
		
	}
</script>

<style scoped lang="scss">
.nothing {
	display: flex;
	justify-content: center;
	align-items: center;
	background: #FFFFFF;
	position: absolute;
	top: 0;
	left: 0;
	right: 0;
	bottom: 0;
	image {
		width: 50%;
	}
}
</style>
