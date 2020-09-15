<template>
	<view class="body">
		<!-- popup弹出框 -->
		<paper-left-popup
		:show="show"
		@hidepopup="hidepopup"
		@addfriend="addfriend"
		@clear="clear"
		></paper-left-popup>
		<!-- 小纸条列表 -->
		<block v-for="(item,index) in list" :key="index">
			<paper-list :item="item"></paper-list>
		</block>
		<load-more :loadtext="loadtext"></load-more>
		
	</view>
</template>

<script>
	import paperList from '../../components/paper/paper-list.vue'
	import loadMore from '../../components/common/load-more.vue'
	import paperLeftPopup from '../../components/paper/paper-left-popup.vue'
	export default {
		components:{
			paperList,
			loadMore,
			paperLeftPopup
		},
		data() {
			return {
				show:false,//是否显示菜单
				loadtext:"上拉加载更多",
				list:[
						{
							userpic:"../../static/demo/userpic/1.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/2.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/3.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/4.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						},
						{
							userpic:"../../static/demo/userpic/5.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/6.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/7.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/8.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						}
					]
			}
		},
		//监听原生标题栏导航按钮点击事件
		onNavigationBarButtonTap(e){
			switch (e.index){
				case 0:
					console.log("点击了左边按钮")
					this.hidepopup()
				break;
				case 1:
					//点击+号
					this.showpopup()
				break;
			}
		},
		onPullDownRefresh() {
			this.getData()
		},
		//页面触底 上拉加载
		onReachBottom() {
			this.loadMore()
		},
		methods: {
			addfriend() {
				console.log("加糗友")
				this.hidepopup()
			},
			clear() {
				console.log("清除缓存")
				this.hidepopup()
			},
			hidepopup() {
				this.show = false
			},
			showpopup() {
				this.show = true
			},
			getData() {
				setTimeout(() => {
					let arr = [
						{
							userpic:"../../static/demo/userpic/11.jpg",
							username:"昵称111",
							time:"10:21",
							data:"我是信息111",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/2.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/3.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/4.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						},
						{
							userpic:"../../static/demo/userpic/5.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:2
						},
						{
							userpic:"../../static/demo/userpic/6.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/7.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:0
						},
						{
							userpic:"../../static/demo/userpic/8.jpg",
							username:"昵称",
							time:"10:21",
							data:"我是信息",
							noreadnum:11
						}
					]
					this.list = arr
					uni.stopPullDownRefresh()
					
				}, 2000);
			},
			loadMore() {
				if(this.loadtext !="上拉加载更多"){return}
				//修改状态
				this.loadtext="加载中..."
				//获取数据
				setTimeout(()=>{
					let obj = {
							userpic:"../../static/demo/userpic/11.jpg",
							username:"昵称111",
							time:"10:21",
							data:"我是信息111",
							noreadnum:2
					};
					this.list.push(obj);
					this.loadtext = "上拉加载更多";
				},1000)
			}
		},
		
	}
</script>

<style lang="scss">
.body {
	padding: 0 20upx;
}



</style>
