<template name="tabbar">
	<view>

		<view class='tab-bar-container'>
			<navigator class="navigator" :class="{'active': index == navActive}" v-for="(item, index) in navs" :key="item.url"
			 open-type="switchTab" :url="item.url" hover-class="none">
			


				<view class="tabImage">
					<image class="tabbarIcon" mode="aspectFill" :src="item.selectedIconPath" v-if="index == navActive"></image>
					<image class="tabbarIcon" mode="aspectFill" :src="item.iconPath" v-else></image>
				</view>
				<view class="text">{{item.text}}</view>
			</navigator>
		</view>


	</view>
</template>

<script>
	export default {
		name: "tabbar",
		data() {
			return {
				currentIndexNav: 0,
				navs: [{
						text: '首页',
						url: '../index/index',
						"iconPath": "/static/images/link-icon1.png",
						"selectedIconPath": "/static/images/link-icon1-hover.png"
					},
					{
						text: '人脸',
						url: '../face/face',
						"iconPath": "/static/images/link-icon2.png",
						"selectedIconPath": "/static/images/link-icon2-hover.png"
					},
				]
			}
		},
		props: {
			// 当前导航高亮
			navActive: {
				// 类型
				type: Number,
				// 默认值
				value: 0
			}
		},
		methods: {

		},
	}
</script>

<style lang="scss" scoped>
	.tab-bar-container {
		position: fixed;
		left: 0;
		bottom: 0;
		z-index: 999;
		width: 100%;
		height: 45px;
		box-shadow: 0 0 6px 0 rgba(0, 0, 0, 0.12);
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 5rpx;
		box-sizing: border-box;
		background-color: #fff;

		.navigator {
			height: 100%;
			width: 50%;
			display: flex;
			flex-wrap: wrap;
			flex-direction: column;
			align-items: center;
			justify-content: center;
			position: relative;
			.tabImage {
				font-size: 0;
				image {
					width: 22px;
					height: 22px;
				}
			}
			.text {
				font-size: 24rpx;
				color: #333;
			}
			&.active {
				.text {
					color: #9c528a;
				}
			}
		}
	}
</style>
