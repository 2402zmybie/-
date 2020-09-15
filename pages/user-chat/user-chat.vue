<template>
	<view>
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

</style>
