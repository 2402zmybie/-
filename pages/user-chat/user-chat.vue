<template>
	<view>
		<!-- 聊天列表 -->
		<block v-for="(item,index) in list" :key="index">
			<view class="user-chat-time u-f-ajc">{{ item.time }}</view>
			<view class="user-chat-list u-f " :class="{'user-chat-me': item.isme}">
				<image v-if="!item.isme" :src="item.userpic" mode="widthFix" lazy-load></image>
				<view class="user-chat-list-body">
					<!-- 文字 -->
					<text v-if="item.type == 'text'">{{ item.data }}</text>
					<!-- 图片 -->
					<image v-if="item.type == 'img'" :src="item.data" mode="widthFix"></image>
				</view>
				
				<!-- 我发送的消息,头像在右边 -->
				<image v-if="item.isme" :src="item.userpic" mode="widthFix" lazy-load></image>
				
			</view>
		</block>
		
		
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
				list:[
					{
						isme:false,
						userpic:"../../static/demo/userpic/11.jpg",
						type:"text",
						data:"哈哈哈",
						time:"1555146412"
					},
					{
						isme:true,
						userpic:"../../static/demo/userpic/10.jpg",
						type:"img",
						data:"../../static/demo/3.jpg",
						time:"1555146414",
					},
					{
						isme:false,
						userpic:"../../static/demo/userpic/11.jpg",
						type:"text",
						data:"哈哈哈",
						time:"1555146412"
					},
					{
						isme:true,
						userpic:"../../static/demo/userpic/10.jpg",
						type:"img",
						data:"../../static/demo/4.jpg",
						time:"1555146414",
					},
					{
						isme:true,
						userpic:"../../static/demo/userpic/10.jpg",
						type:"img",
						data:"../../static/demo/4.jpg",
						time:"1555146414",
					}
				]
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
.user-chat-time {
	padding: 50upx 0;
	color: #a2a2a2;
	font-size: 24upx;
}
.user-chat-list {
	padding: 20upx;
	>image {
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
		image {
			max-width: 200upx;
			max-height: 150upx;
		}
	}
}
.user-chat-me {
	justify-content: flex-end;
	.user-chat-list-body {
		margin-right: 20upx;
		margin-left: 100upx;
		:after {
			left: auto;
			right: -30upx;
			border-color: transparent  transparent transparent #F4F4F4;
		}
	}
}
</style>
