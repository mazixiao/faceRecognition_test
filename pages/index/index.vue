<template>
	<view class="content">
		<headers title="首页" :show_logo="true" :show_bol="true" :show_title="false" backgroundColor="#fff"></headers>
		<!-- :style="{ color: activeColor, fontSize: fontSize + 'px' }" -->
		<!-- <view :style="padding-top:{{bar_Height  + 45}}px;background: #ffffff"></view> -->
		<view class="aa" :style="{'padding-top': bar_Height + 45 + 'px','background':  '#ffffff'}"></view>
		<tabBar navActive='0'></tabBar>






		<view class="page-body">
			<view class="page-body-wrapper">
				<camera device-position="front" flash="off" binderror="error" style="width: 100%; height: 300px;"></camera>
				<view class="btn-area">
					<button type="primary" @click="takePhoto">拍照0</button>
				</view>
				<view class="btn-area">
					<button type="primary" @click="startRecord">开始录像</button>
				</view>
				<view class="btn-area">
					<button type="primary" @click="stopRecord">结束录像</button>
				</view>
				<view class="preview-tips">预览</view>
				<image v-if="src" mode="widthFix" :src="src"></image>
				<video v-if="videoSrc" class="video" :src="videoSrc"></video>
			</view>
		</view>


<van-button type="primary">主要按钮</van-button>



	</view>
</template>

<script>
	import headers from "../../components/headers.vue"
	import tabBar from '../../components/tabbar.vue'
	export default {
		name: "index",
		components: {
			headers,
			tabBar,
			// 当前tab高亮索引
		},
		data() {
			return {
				bar_Height: wx.getSystemInfoSync().statusBarHeight,
				src: '',
				videoSrc: '',
			}
		},
		onLoad() {
			uni.hideTabBar({
				animation: false
			});
			console.log(this.bar_Height)

			this.ctx = wx.createCameraContext()






		},
		methods: {

			// 拍照
			takePhoto() {
				const ctx = uni.createCameraContext()
				ctx.takePhoto({
					quality: 'high',
					success: (res) => {
						console.log(res)
						this.src = res.tempImagePath

					}
				})
			},
			// 开始录像
			startRecord() {
				this.ctx.startRecord({
					success: (res) => {
						console.log('startRecord')
					}
				})
			},
			// 结束录像
			stopRecord() {
				this.ctx.stopRecord({
					success: (res) => {
							this.src = res.tempThumbPath,
							this.videoSrc = res.tempVideoPath
					}
				})
			},
			error(e) {
				console.log(e.detail)
			}

		}
	}
</script>
<style lang="scss" scoped>
	@import 'index.scss';
</style>
