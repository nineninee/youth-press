<template>
	<view class="user">
		<view class="top">
			<image src="../../static/images/history.png" mode=""></image>
			<text>浏览历史</text>
		</view>
		<view class="content">
			<view class="row" v-for="item in 10">
				<newsbox @click.native="goDetail"></newsbox>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			goDetail(){
				uni.navigateTo({
					url:"/pages/detail/detail"
				})
			}
		}
	}
</script>

<style lang="scss">
.user{
	.top{
		padding: 50rpx 0;
		background: #f8f8f8;
		color: #666;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		image{
			width: 150rpx;
			height: 150rpx;
		}
		text{
			font-size: 38rpx;
			padding-top: 20rpx;
		}
	}
		
	.content{
		padding: 30rpx;
		.row{
			border-bottom: 1px dotted #efefef;
			padding: 20rpx 0;
		}
	}
}
</style>
