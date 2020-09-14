<template>
	<view class="body">
		<!-- 操作菜单 -->
		<view class="paper-left-popup-mask" v-show="show" @tap="hidepopup"></view>
		<view class="paper-left-popup" v-show="show">
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="addfriend">
				<view class="icon iconfont icon-sousuo"></view>
				加糗友
			</view>
			<view style="height: 1px; background: #CCCCCC;"></view>
			<view class="u-f-ac" hover-class="paper-left-popup-h" @tap="clear">
				<view class="icon iconfont icon-qingchu"></view>
				清除缓存
			</view>
		</view>
		
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
	export default {
		components:{
			paperList,
			loadMore
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
				console.log(111)
				this.hidepopup()
			},
			clear() {
				console.log(222)
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

.paper-left-popup-mask {
	position: fixed;
	right: 0;
	left: 0;
	top: 0;
	bottom: 0;
	z-index: 1999;
	
}
.paper-left-popup {
	position: fixed;
	right: 0;
	top: 10upx;
	background: #FFFFFF;
	z-index: 2000;
	width: 55%;
	box-shadow: 1upx 1upx 20upx #CCCCCC;
	>view:nth-child(1), view:nth-child(3){
		padding: 20upx;
		font-size: 35upx;
		>view {
			margin-right: 10upx;
			font-weight: bold;
		}
	}
}
.paper-left-popup-h {
	background: #EEEEEE;
}

</style>
