<template>
	<view>
		<swiper-tab-head :tabBars = "tabBars" :tabIndex = "tabIndex" @tabtap="tabtap"></swiper-tab-head>
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height: swiperheight + 'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y="true" class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length > 0">
							<!-- 话题分类列表 -->
							<view class="topic-view">
								<block v-for="(item,index1) in items.list" :key="index1">
									<topic-list :item="item"></topic-list>
								</block>
							</view>
							<!-- 上拉加载更多 -->
							<load-more :loadtext="items.loadtext"></load-more>
						</template>
						<template v-else>
							<!-- 无内容默认 -->
							<no-thing></no-thing>
						</template>
					</scroll-view>
				</swiper-item>
			</swiper>
		</view>
	</view>
</template>

<script>
	import swiperTabHead from '../../components/index/swiper-tab-head.vue'
	import loadMore from '../../components/common/load-more.vue'
	import noThing from '../../components/common/no-thing.vue'
	import topicList from '../../components/news/topic-list.vue'
	export default {
		components: {
			swiperTabHead,
			loadMore,
			noThing,
			topicList
		},
		data() {
			return {
				swiperheight:500,//高度
				tabIndex:0,// 选中的
				tabBars:[
					{ name:"关注",id:"guanzhu" },
					{ name:"推荐",id:"tuijian" },
					{ name:"体育",id:"tiyu" 	  },
					{ name:"热点",id:"redian"  },
					{ name:"财经",id:"caijing" },
					{ name:"娱乐",id:"yule"    },
				],
				newslist:[
					{
						loadtext:"上拉加载更多",
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
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/3.jpeg",
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/4.jpeg",
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							{
								titlepic:"/static/demo/topicpic/3.jpeg",
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							},
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[{
								titlepic:"/static/demo/topicpic/10.jpeg",
								title:"话题名称5",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							},
							{
								titlepic:"/static/demo/topicpic/8.jpeg",
								title:"话题名称1",
								desc:"我是话题描述1",
								totalnum:50,
								todaynum:10
							}]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					},
					{
						loadtext:"上拉加载更多",
						list:[]
					}
				],
			}
		},
		methods: {
			tabtap(index) {
				this.tabIndex = index
			},
			tabChange(e) {
				this.tabIndex = e.detail.current
			},
			loadmore(index) {
				//上拉加载
				if(this.guanzhu.loadtext !="上拉加载更多"){return}
				//修改状态
				this.guanzhu.loadtext="加载中..."
				//获取数据
				setTimeout(()=>{
					let obj = {
						titlepic:"/static/demo/topicpic/1.jpeg",
						title:"话题名称1",
						desc:"我是话题描述1",
						totalnum:50,
						todaynum:10
					};
					this.guanzhu.list.push(obj);
					this.guanzhu.loadtext = "上拉加载更多";
				},1000)
			}
		}
	}
</script>

<style lang="scss">
.topic-view {
	padding: 0 20upx;
}
</style>
