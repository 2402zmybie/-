<template>
	<view>
		<!-- 自定义导航栏 -->
		<news-nav-bar :tabIndex="tabIndex" :tabBars="tabBars" @change-tab="changeTap"></news-nav-bar>
		<!-- 列表 -->
		<block v-for="(item,index) in guanzhu.list" :key="index">
			<common-list :item="item" :index="index"></common-list>
		</block>
		
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	//头部导航
	import newsNavBar from "../../components/news/news-nav-bar.vue"
	//话题列表
	import commonList from '../../components/common/common-list.vue'
	export default {
		components:{
			uniNavBar,
			newsNavBar,
			commonList
		},
		data() {
			return {
				swiperheight:500,//屏幕高度
				tabIndex:1,//tab索引
				tabBars:[
					{name:"关注",id:"guanzhu"},
					{name:"话题",id:"huati"}
				],
				topic:{
					swiper:[
						{src:"/static/demo/banner1.jpg"},
						{src:"/static/demo/banner2.jpg"},
						{src:"/static/demo/banner3.jpg"}
					],
					nav:[
						{name:"最新"},
						{name:"游戏"},
						{name:"打开"},
						{name:"情感"},
						{name:"故事"},
						{name:"喜爱"},
					],
					list:[
							{
								titlepic:"/static/demo/topicpic/1.jpeg",
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/2.jpeg",
								title:"话题名称2",
								desc:"我是话题描述2",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/3.jpeg",
								title:"话题名称3",
								desc:"我是话题描述3",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/4.jpeg",
								title:"话题名称5",
								desc:"我是话题描述5",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/5.jpeg",
								title:"话题名称4",
								desc:"我是话题描述4",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/6.jpeg",
								title:"话题名称6",
								desc:"我是话题描述6",
								totalnum:50,
								todaynum:10
							}
						]
				},
				guanzhu:{
					loadtext:"上拉加载更多",
					list:[
						// 文字
						{
							userpic:"../../static/demo/userpic/2.jpg",
							username:"哈哈",
							sex:1, //0 男 1 女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						// 图文
						{
							userpic:"../../static/demo/userpic/1.jpg",
							username:"哈哈",
							sex:0, //0 男 1 女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"../../static/demo/datapic/13.jpg",
							video:false,
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						// 视频
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈",
							sex:1, //0 男 1 女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"../../static/demo/datapic/13.jpg",
							video:{
								looknum:"20w",
								long:"2:47"
							},
							share:false,
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
						// 分享
						{
							userpic:"../../static/demo/userpic/12.jpg",
							username:"哈哈",
							sex:0, //0 男 1 女
							age:25,
							isguanzhu:false,
							title:"我是标题",
							titlepic:"",
							video:false,
							share:{
								title:"我是分享的标题",
								titlepic:"../../static/demo/datapic/14.jpg"
							},
							path:"深圳 龙岗",
							sharenum:20,
							commentnum:30,
							goodnum:20
						},
					]
				},
			}
		},
		methods: {
			changeTap(index) {
				this.tabIndex = index;
			}
		}
	}
</script>

<style lang="scss">

	

</style>
