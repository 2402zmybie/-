<template>
	<view>
		<block  v-for="(item,index) in list" :key="index">
			<indexList :item="item" :index="index"></indexList>
		</block>
	</view>
</template>

<script>
	import indexList from '../../components/index/index-list.vue';
	export default {
		components:{
			indexList
		},
		data() {
			return {
				list:[{
					userpic:"../../static/demo/userpic/12.jpg",
					username:"小何",
					title:"我是标题",
					isguanzhu:true,
					type: "video", //img图文, video视频
					titlepic:"../../static/demo/datapic/11.jpg",
					playnum:"20w",
					long:"2:47",
					infonum: {
						//0:没有操作, 1 顶 2踩
						index:1,
						dingnum:11,
						cainum:11
					},
					commentnum:10,
					sharenum:10
				}]
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style >

</style>
