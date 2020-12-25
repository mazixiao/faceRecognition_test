<template>
	<view class="content">
		<headers title="人脸" :show_logo="true" :show_bol="true" :show_title="false" backgroundColor="#fff"></headers>
		<tabBar navActive='1'></tabBar>
		<view class="text-area">
			<text class="title">{{title}}</text>
			<van-button type="primary">按钮</van-button>
		</view>
	</view>
</template>

<script>
	import headers from "../../components/headers.vue";
	import tabBar from '../../components/tabbar.vue';
	export default {
		name: "face",
		components: {
			headers,
			tabBar,
			// 当前tab高亮索引
		},
		data() {
			return {
				title: '脸'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>
<style lang="scss" scoped>
	@import 'face.scss';
</style>
