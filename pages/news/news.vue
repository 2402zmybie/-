<template>
	<view>
		<!-- 自定义导航栏 -->
		<news-nav-bar :tabIndex="tabIndex" :tabBars="tabBars" @change-tab="changeTap"></news-nav-bar>

		
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height: swiperheight + 'px'}" :current="tabIndex" @change="tabChange">
				<!-- 关注 -->
				<swiper-item >
					<scroll-view scroll-y="true" class="list" @scrolltolower="loadmore()">
						<!-- 列表 -->
						<block v-for="(item,index) in guanzhu.list" :key="index">
							<common-list :item="item" :index="index"></common-list>
						</block>
						<!-- 上拉加载 -->
						<load-more :loadtext="guanzhu.loadtext"></load-more>
					</scroll-view>
				</swiper-item>
				<!-- 话题 -->
				<swiper-item >
					<scroll-view scroll-y="true" class="list">
						<!-- 搜索框 -->
						<view class="search-input">
							<input placeholder="搜索内容" placeholder-class="icon iconfont icon-sousuo topic-search "/>
						</view>
						<!-- 轮播图 -->
						<swiper class="topic-swiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
							<swiper-item v-for="(item,index) in topic.swiper" :key="index">
								<image :src="item.src" mode="aspectFill" lazy-load></image>
							</swiper-item>
						</swiper>
						<!-- 热门分类 -->
						<topic-nav :navs="topic.nav" @openTopicNav="openTopicNav"></topic-nav>
						<!-- 最近更新 -->
						<view class="topic-new">
							<view>最近更新</view>
							<block v-for="(item,index) in topic.list" :key="index">
								<topic-list :item="item" ></topic-list>
							</block>
						</view>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
		
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar.vue"
	//头部导航
	import newsNavBar from "../../components/news/news-nav-bar.vue"
	//关注列表
	import commonList from '../../components/common/common-list.vue'
	//加载更多
	import loadMore from '../../components/common/load-more.vue'
	//话题--热门分类
	import topicNav from '../../components/news/topic-nav.vue'
	//话题--列表项
	import topicList from '../../components/news/topic-list.vue'
	export default {
		components:{
			uniNavBar,
			newsNavBar,
			commonList,
			loadMore,
			topicNav,
			topicList
		},
		onLoad() {
			//获取可用窗口的高度
			uni.getSystemInfo({
				success: (res) => {
					//获取下方滑动的ListView容器的高度
					let height = res.windowHeight - uni.upx2px(100)
					console.log(height)
					this.swiperheight = height
				}
			})
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
			openTopicNav() {
				uni.navigateTo({
					url: '../topic-nav/topic-nav'
				});
			},
			//点击切换
			changeTap(index) {
				this.tabIndex = index;
			},
			//ListView swiper切换,滑动切换
			tabChange(e) {
				this.tabIndex = e.detail.current
			},
			//关注上拉加载
			loadmore() {
				//上拉加载
				if(this.guanzhu.loadtext !="上拉加载更多"){return}
				//修改状态
				this.guanzhu.loadtext="加载中..."
				//获取数据
				setTimeout(()=>{
					let obj = {
						userpic:"../../static/demo/userpic/12.jpg",
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
					};
					this.guanzhu.list.push(obj);
					this.guanzhu.loadtext = "上拉加载更多";
				},1000)
			}
		
		}
	}
</script>

<style lang="scss">
.search-input {
	padding: 20upx;
	input {
		background: #F4F4F4;
		border-radius: 10upx;
		padding: 10upx 0;
	}
	.topic-search {
		display: flex;
		justify-content: center;
		font-size: 27upx;
	}
}
// 轮播图
.topic-swiper {
	padding: 20upx;
	image {
		width: 100%;
		border-radius: 10upx;
	}
}


//话题列表
.topic-new {
	padding: 20upx;
	>view:first-child {
		padding-bottom: 5upx;
		font-size: 32upx;
	}
}


	

</style>
