<template>
	<view class="home">
		<scroll-view scroll-x="true" class="navscroll">
			<view class="item" :class="navIndex===index?'active':''" v-for="(item, index) in 10"
				@click="clickNav(index)">国内</view>
		</scroll-view>

		<view class="content">
			<div class="row" v-for="item in 10">
				<newsbox @click.native="goDetail"></newsbox>
			</div>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navIndex: 0,
			}
		},
		onLoad() {

		},
		methods: {
			clickNav(index){
				this.navIndex = index
			},
			goDetail(){
				uni.navigateTo({
					url:"/pages/detail/detail",
				})
			}
		}
	}
</script>
<strong></strong>
<style lang="scss" scoped>
	.navscroll {
		height: 100rpx;
		white-space: nowrap;
		background: #F7FBFA;
		position: fixed;
		top: var(--window-top);
		left: 0;
		z-index: 10;

		/deep/ ::-webkit-scrollbar {
			width: 4px !important;
			height: 1px !important;
			overflow: auto !important;
			background: transparent !important;
			-webkit-appearance: auto !important;
			display: block;
		}

		.item {
			font-size: 40rpx;
			display: inline-block;
			padding: 0 30rpx;
			line-height: 100rpx;
			color: #333;
			&.active{
				color: #31c27c;
			}
		}

	}

	.content {
		padding: 30rpx;
		padding-top: 100rpx;

		.row {
			border-bottom: 1px dotted #efefef;
			padding: 20rpx 0;
		}
	}
</style>