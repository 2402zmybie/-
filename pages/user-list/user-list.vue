<template>
	<view class="body">
		<!-- tab切换 -->
		<swiper-tab-head
			:tabBars = "tabBars" 
			:tabIndex = "tabIndex" 
			@tabtap="tabtap"
			scrollStyle="border-bottom:0;"
			scrollItemStyle="width:33%"
		></swiper-tab-head>
		<!-- 好友列表 -->
		<view class="uni-tab-bar">
			<swiper class="swiper-box" :style="{height: swiperheight + 'px'}" :current="tabIndex" @change="tabChange">
				<swiper-item v-for="(items,index) in newslist" :key="index">
					<scroll-view scroll-y="true" class="list" @scrolltolower="loadmore(index)">
						<template v-if="items.list.length > 0">
							<!-- 列表 -->
							<block v-for="(item,index1) in items.list" :key="index1">
								<user-list :item="item" :index="index"></user-list>
							</block>
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
	import userList from '../../components/user-list/user-list.vue'
	import loadMore from '../../components/common/load-more.vue'
	export default {
		components: {
			swiperTabHead,
			userList,
			loadMore
		},
		onLoad() {
			//获取可用窗口的高度
			uni.getSystemInfo({
				success: (res) => {
					//获取下方滑动的ListView容器的高度
					let height = res.windowHeight - uni.upx2px(100)
					this.swiperheight = height
				}
			})
		},
		data() {
			return {
				swiperheight:500,//高度
				tabIndex:0,// 选中的
				tabBars:[
					{ name:"互关",id:"huguan",num:10 },
					{ name:"关注",id:"guanzhu",num:20  },
					{ name:"粉丝",id:"fensi",num:30  }
				],
				newslist:[
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:"../../static/demo/userpic/1.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/2.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:"../../static/demo/userpic/9.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/10.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:"../../static/demo/userpic/14.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/15.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							},
							{
								userpic:"../../static/demo/userpic/16.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/17.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:"../../static/demo/userpic/3.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/4.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							}
						]
					},
					{
						loadtext:"上拉加载更多",
						list:[
							{
								userpic:"../../static/demo/userpic/5.jpg",
								username:"昵称",
								age:20,
								sex:0,
								isguanzhu:true
							},
							{
								userpic:"../../static/demo/userpic/6.jpg",
								username:"昵称",
								age:21,
								sex:1,
								isguanzhu:false
							}
						]
					}
				]
				
			}
		},
		methods:{
			tabtap(index) {
				this.tabIndex = index
			},
			tabChange(e) {
				this.tabIndex = e.detail.current
			},
			loadmore(index){
				if(this.newslist[index].loadtext !="上拉加载更多"){return}
				//修改状态
				this.newslist[index].loadtext="加载中..."
				//获取数据
				setTimeout(()=>{
					let obj = {
						userpic:"../../static/demo/userpic/12.jpg",
						username:"加载",
						age:22,
						sex:1,
						isguanzhu:false
					};
					this.newslist[index].list.push(obj);
					this.newslist[index].loadtext = "上拉加载更多";
				},1000)
			}
		},
		//监听导航按钮事件
		onNavigationBarButtonTap(e) {
			//点击取消按钮
			if(e.index == 0) {
				uni.navigateBack({
					delta: 1
				});
			}
		}
	}
</script>

<style lang="scss">


</style>
