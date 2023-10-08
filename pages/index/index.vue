<template>
	<view class="home">
		<scroll-view scroll-x="true" class="navscroll">
			<view 
			class="item" 
			:class="navIndex===index?'active':''" 
			v-for="(item, index) in navArr"
			:key="item.id"
			@click="clickNav(index, item.id)">{{item.classname}}</view>
		</scroll-view>

		<view class="content">
			<div class="row" v-for="item in newsArr" :key="item.id">
				<newsbox @click.native="goDetail" :item="item"></newsbox>
			</div>
		</view>
		<view class="nodata" v-if="!newsArr.length" mode="widthFix">
			<image src="../../static/images/nodata.png"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				navArr: [],
				navIndex: 0,
				newsArr:[]
			}
		},
		onLoad() {
			this.getNavData()
			this.getNewsData()
		},
		methods: {
			clickNav(index, id){
				this.navIndex = index
				this.getNewsData(id)
			},
			goDetail(){
				uni.navigateTo({
					url:"/pages/detail/detail",
				})
			},
			getNavData(){
				uni.request({
					url:"https://ku.qingnian8.com/dataApi/news/navlist.php",
					success:res=>{
						console.log(res)
						this.navArr = res.data
					}
				})
			},
			getNewsData(id=50){
				uni.request({
					url:"https://ku.qingnian8.com/dataApi/news/newslist.php",
					data:{
						cid:id
					},
					success:res=>{
						console.log(res)
						this.newsArr = res.data
					}
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
	.nodata{
		display: flex;
		justify-content: center;
		image{
			width: 360rpx;
		}
	}
</style>