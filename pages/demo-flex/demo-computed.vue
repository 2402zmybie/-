<template>
	<view>
		<text>需求: 如果体重大于1000则显示...kg, 否则显示...g\n
			 计算属性:\n
		</text>
		<text class="tx">
			体重: {{ transferWeight }}
		</text>
		<button type="primary" @tap="addWeight">增加体重</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				weight:900
			}
		},
		computed:{
			transferWeight() {
				return this.weight > 1000 ? (this.weight /1000) + "kg" : this.weight + "g"
			}
		},
		methods: {
			addWeight() {
				this.weight += 40
			}
		}
	}
</script>

<style>
.tx {
	font-size: 30upx;
	color: #FF0000;
	margin: 10upx auto;
}
</style>
