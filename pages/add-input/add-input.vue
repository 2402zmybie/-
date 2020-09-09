<template>
	<view>
		<!-- 自定义导航栏 -->
		<uni-nav-bar :statusBar="true" rightText="发布" left-icon="back" @clickLeft="back" @clickRight="submit">
			<view class="title-slot" @tap="changelook">
				{{ yinsi }}
				<view class="icon iconfont icon-xialazhankai"></view>
			</view>
		</uni-nav-bar>
		<!-- 多行输入框 -->
		<view class="uni-textarea">
			<textarea placeholder="说一句话吧" v-model="text"></textarea>
		</view>
		<!-- 上传多图 -->
		<upload-images @uploadImage="uploadImage"></upload-images>
		<!-- 弹出公告 -->
		<uni-popup id="popup" ref="popup" :type="type" :animation="false" @change="change">
			<view class="popup-content">popup 内容，此示例没有动画效果</view>
		</uni-popup>
	</view>
</template>

<script>
	import uniNavBar from "../../components/uni-nav-bar/uni-nav-bar";
	import uploadImages from '../../components/common/upload-images.vue'
	//弹出层
	import {uniPopup} from '@dcloudio/uni-ui'
	let changelook = ['所有人可见', '仅自己可见'];
	export default {
		components: {
			uniNavBar,
			uploadImages,
			
		},
		data() {
			return {
				yinsi: "所有人可见",
				text: '',
				imageList:[],
				
				type: 'center',
				msgType: 'success',
				message: '这是一条成功消息提示',
				value: '默认输入的内容'
			}
		},
		methods: {
			//弹出层改变事件
			change() {
				
			},
			uploadImage(imageList) {
				this.imageList = imageList;
				console.log(this.imageList)
			},
			back() {
				console.log(111)
				uni.navigateBack({
					delta: 1
				});
			},
			changelook() {
				uni.showActionSheet({
				    itemList: changelook,
				    success: (res) => {
				       this.yinsi = changelook[res.tapIndex]
				    },
				});
			},
			submit() {
				console.log("发布")
			}
		}
	}
</script>

<style lang="scss">
.title-slot {
	display: flex;
	justify-content: center;
	align-items: center;
}

.uni-textarea {
	border: 1px solid #EEEEEE;
}

.cell-pd {
	padding: 22rpx 30rpx;
}

.list-pd {
	margin-top: 50rpx;
}



</style>
