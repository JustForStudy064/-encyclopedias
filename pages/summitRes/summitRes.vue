<template>
	<view>
		<view class="title">提交结果</view>
		<view class="summit-pic">这里是一张图片，还没有画好呜呜~</view>
		<view class="thanks-text">感谢小主人对灯灯的支持～</view>
		<view class="thanks-text" style="font-size: 26rpx;">如有任何疑惑可以召唤灯灯哦～</view>
		<view class="back-container">
			<view class="back-item" @click="backLesson">返回课程</view>
			<view class="back-item" @click="backIndex">返回首页</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			backLesson(){
				uni.switchTab({
					url: "/pages/course/course"
				})
			},
			backIndex(){
				uni.switchTab({
					url: "/pages/index/index"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
  .title{
		margin: 42rpx 0 0 54rpx;
		font-size: 52rpx;
		
	}
	
	.summit-pic{
		height: 352rpx;
		width: 616rpx;
		border: 2rpx solid #707070;
		margin: 0 66rpx 54rpx;
	}
	
	.thanks-text{
		color: #000;
		font-size: 36rpx;
		line-height: 48rpx;
		margin-left:66rpx;
	}
	
	.back-container{
		margin-top: 44rpx;
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		.back-item{
			background: #F7E598;
			line-height: 46rpx;
			font-size: 26rpx;
			padding: 16rpx 30rpx 14rpx;
			border-radius: 100rpx;
		}
	}
	

</style>
