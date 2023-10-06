<template>
	<view class="home">
		<scroll-view scroll-x="true" class="navscroll">
			<view class="item" v-for="item in 10">国内</view>
		</scroll-view>
		
		<view class="content">
			<div class="row">每一行的新闻</div>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	
.navscroll{
	height: 100rpx;
	white-space: nowrap;
	background: #F7FBFA;
	/deep/ ::-webkit-scrollbar{
		width: 4px !important;
		height: 1px !important;
		overflow: auto !important;
		background: transparent !important;
		-webkit-appearance: auto !important;
		display: block;
	}
	.item{
		font-size: 40rpx;
		display: inline-block;
		padding: 0 30rpx;
		line-height: 100rpx;
		color: #333;
	}
	
}
</style>
