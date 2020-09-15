<template>
	<view>
		<!-- 聊天列表 -->
		<view class="user-chat-list u-f">
			<image src="../../static/demo/userpic/1.jpg" mode="widthFix" lazy-load></image>
			<view class="user-chat-list-body">
				<text>你好亚</text>
			</view>
		</view>
		
		<!-- 输入框 -->
		<user-chat-bottom @submit="submit"></user-chat-bottom>
	</view>
</template>

<script>
	import userChatBottom from '../../components/user-chat/user-chat-bottom.vue'
	export default {
		components:{
			userChatBottom
		},
		data() {
			return {
				
			}
		},
		methods: {
			submit(input) {
				console.log(input)
			}
		}
	}
</script>

<style lang="scss">
.user-chat-list {
	image {
		width: 100upx;
		height: 100upx;
		border-radius: 100%;
		flex-shrink: 0;
		
	}
	.user-chat-list-body {
		position: relative;
		background: #F4F4F4;
		padding: 25upx;
		margin-left: 20upx;
		margin-right: 100upx;
		border-radius: 20upx;
		:after {
			position: absolute;
			left: -30upx;
			right: 0;
			top: 30upx;
			content: '';
			width: 0;
			height: 0;
			border: 16upx solid #F4F4F4;
			border-color: transparent #F4F4F4 transparent transparent;
		}
	}
}
</style>
