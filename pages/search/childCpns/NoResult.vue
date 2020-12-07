<template>
	<view id="no_result">
		<image src="@/static/search/notResult.png" class="no_result_image"></image>
		<view class="no_result_text">灯灯费了九牛二虎之力都没有找到相关结果···</view>
	</view>
</template>

<script>
	export default {
		name: "NoResult",
		data() {
			return {
				
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
</style>
