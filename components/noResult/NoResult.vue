<template>
	<view>
		<view>
			<image src="@/static/search/notResult.png" class="no_result_image"></image>
			<view class="no_result_text">灯灯费了九牛二虎之力都没有找到相关结果···</view>
		</view>
		
		<!-- <view style="position: relative; margin-top: 56rpx;">
			<view class="info_title">
				没有找到想要的结果？
			</view>
			<view class="info_text">
				{{info_text_desc}}
			</view>
			<view class="bottom_btn">召唤灯神</view>
		</view> -->
	</view>
</template>

<script>
	export default {
		name: "NoResult",
		data() {
			return {
				// info_text_desc: "去“我的小灯神”上发个悄悄话或心愿寻求帮助吧!"
			}
		}
	}
</script>

<style scoped>
	.no_result_image{
		width: 422rpx;
		height: 240rpx;
		margin: 78rpx 164rpx 34rpx;
	}
	
	.no_result_text{
		color: #000;
		font-size: 26rpx;
		margin-left: 102rpx;
	}
	
	.bottom-info{
		padding: 30rpx 58rpx 0 56rpx;
		height: 184rpx;
		position: relative;
	}
	
	.info_title{
		font-size: 34rpx;
		padding-bottom: 20rpx;
		padding-left: 56rpx;
		color: #404040;
	}
	
	.info_text{
		color: #404040;
		font-size: 26rpx;
		padding-left: 56rpx;
	}
	
	.bottom_btn{
		padding: 16rpx 24rpx 14rpx;
		border-radius: 28rpx;
		margin: 14rpx 56rpx 0 0;
		font-size: 26rpx;
		background: #F7E598;
		width: 104rpx;
		color: #000;
		float: right;
	}
</style>
