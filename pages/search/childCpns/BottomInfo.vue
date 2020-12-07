<template>
	<view class="bottom-info">
		<view class="info_title">
			没有找到想要的结果？
		</view>
		<view class="info_text">
			{{info_text_desc}}
		</view>
		<view class="bottom_btn">召唤灯神</view>
	</view>
</template>

<script>
	export default {
		name: "BottomInfo",
		data(){
			return {
				info_text_desc: "去“我的小灯神”上发个悄悄话或心愿寻求帮助吧!"
			}
		}
	}
</script>

<style>
	.bottom-info{
		padding: 30rpx 58rpx 0 56rpx;
		height: 184rpx;
		position: relative;
	}
	
	.info_title{
		font-size: 34rpx;
		padding-bottom: 20rpx;
		color: #404040;
	}
	
	.info_text{
		color: #404040;
		font-size: 26rpx;
	}
	
	.bottom_btn{
		position: absolute;
		padding: 16rpx 24rpx 14rpx;
		background: #F7E598;
		border-radius: 28rpx;
		width: 104rpx;
		font-size: 26rpx;
		color: #000;
		bottom: 0;
		right: 58rpx;
	}
</style>
