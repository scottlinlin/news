<template>
	<view class="content">
		<!-- <view class="customize-view">
			<text style="width: 100%;">2019年11月27号</text>
			<text class="d-right">自定义查询</text>
		</view> -->
		<view class="uni-list">
			<view class="uni-list-cell" hover-class="uni-list-cell-hover" v-for="(item,index) in news" :key="index">
				<view class="uni-media-list">
					<!-- <image class="uni-media-list-logo" :src="item.author_avatar"></image> -->
					<view class="uni-media-list-body">
						<view class="uni-media-list-text-top">{{item.title}}</view>
						<view class="uni-media-list-text-bottom uni-ellipsis">{{item.created_at}}</view>
						<text class="d-right">12</text>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				news: []
			}
		},
		onLoad() {
			uni.request({
				url: 'https://unidemo.dcloud.net.cn/api/news',
				method: 'GET',
				data: {},
				success: res => {
					console.log(res);
					this.news = res.data;
				},
				fail: () => {},
				complete: () => {}
			});
		},
		methods: {

		}
	}
</script>

<style>
.uni-media-list-body{height: auto;}
.uni-media-list-text-top{line-height:1.6em;}
.d-right {
	text-align: right;
	width: 100%;
	color: blue;
}
</style>
