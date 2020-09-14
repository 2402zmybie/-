<template>
	<view>
		<!-- 上方到 我是描述 -->
		<topic-info :item="topicInfo"></topic-info>
		<!-- tab标签 -->
		<swiper-tab-head 
			:tabBars = "tabBars" 
			:tabIndex = "tabIndex" 
			@tabtap="tabtap"
			scrollStyle="border-bottom:0;"
			scrollItemStyle="width:50%"
		></swiper-tab-head>
		<!-- 列表 -->
		<view class="topic-detail-list">
			<block v-for="(item,index) in tablist" :key="index">
				<template v-if="tabIndex == index">
					<!-- 列表 -->
					<block v-for="(itemlist,itemIndex) in item.list" :index="itemIndex">
						<common-list :item="itemlist" :index="itemIndex"></common-list>
					</block>
					<!-- 上拉加载 -->
					<load-more :loadtext="item.loadtext"></load-more>
				</template>
			</block>
		</view>
	</view>
</template>

<script>
	import topicInfo from '../../components/topic/topic-info.vue'
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	import commonList from '../../components/common/common-list.vue'
	import loadMore from '../../components/common/load-more.vue'
	export default {
		components:{
			topicInfo,
			swiperTabHead,
			commonList,
			loadMore
		},
		data() {
			return {
				topicInfo:{
					titlepic:"/static/demo/topicpic/12.jpeg",
					title:"忆往事，敬余生",
					desc:"我是描述",
					totalnum:1000,
					todaynum:1000,
				},
				tabIndex:0,// 选中的
				tabBars:[
					{ name:"默认",id:"moren" },
					{ name:"最新",id:"zuixin" }
				],	
				tablist:[
					{
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
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							// 文字
							{
								userpic:"../../static/demo/userpic/8.jpg",
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
								userpic:"../../static/demo/userpic/9.jpg",
								username:"哈哈",
								sex:0, //0 男 1 女
								age:25,
								isguanzhu:false,
								title:"我是标题",
								titlepic:"../../static/demo/datapic/10.jpg",
								video:false,
								share:false,
								path:"深圳 龙岗",
								sharenum:20,
								commentnum:30,
								goodnum:20
							},
							// 视频
							{
								userpic:"../../static/demo/userpic/18.jpg",
								username:"哈哈",
								sex:1, //0 男 1 女
								age:25,
								isguanzhu:false,
								title:"我是标题",
								titlepic:"../../static/demo/datapic/16.jpg",
								video:{
									looknum:"20w",
									long:"2:47"
								},
								share:false,
								path:"深圳 龙岗",
								sharenum:20,
								commentnum:30,
								goodnum:20
							}
						]
					}
				]
			}
		},
		methods: {
			tabtap(index) {
				this.tabIndex = index
			},
			loadmore(){
				//上拉加载
				if(this.tablist[this.tabIndex].loadtext !="上拉加载更多"){return}
				//修改状态
				this.tablist[this.tabIndex].loadtext="加载中..."
				//获取数据
				setTimeout(()=>{
					let obj = {
						userpic:"../../static/demo/userpic/16.jpg",
						username:"哈哈",
						sex:1, //0 男 1 女
						age:22,
						isguanzhu:false,
						title:"上拉加载",
						titlepic:"../../static/demo/datapic/15.jpg",
						video:false,
						share:false,
						path:"深圳 龙岗",
						sharenum:20,
						commentnum:30,
						goodnum:20
					};
					this.tablist[this.tabIndex].list.push(obj);
					this.tablist[this.tabIndex].loadtext = "上拉加载更多";
				},1000)
				
			}
			
		},
		//页面触底, 上拉加载的逻辑
		onReachBottom() {
			this.loadmore()
		}
	}
</script>

<style lang="scss">

</style>
