<template>
	<view class="list-item">
		<view class="item_title">
			{{itemDesc.title}}
		</view>
		<view class="right_array"> > </view>
		<view class="item_text">
			{{classify_text}}
		</view>
	</view>
</template>

<script>
	export default {
		name: "ListItem",
		props: ["itemDesc"],
		data(){
			return {
				classify_text: ''
			}
		},
		mounted(){
			this.$data.classify_text = this.$props.itemDesc.classify.join(" · ")
		}
	}
</script>

<style scoped>
	.list-item{
		height: 104rpx;
		margin: 30rpx 30rpx 0rpx 54rpx;
		border-bottom: 2rpx solid #eee;
		position: relative;
	}
	
	.outer_box{
		border: 2rpx solid #000;
	}
	
	.item_title{
		color: #000000;
		font-size: 40rpx;
		margin-bottom: 6rpx;
		width: 90%;
		overflow: hidden;
		/* 溢出的文字用...表示 */
		text-overflow: ellipsis;
		/* 规定段落中的文字不能换行 */
		white-space: nowrap;
	}
	
	.item_text{
		color:#54B1FF;
		font-size: 26rpx;
	}
	
	.classify_item{
		display: inline-block;
	}
	
	.right_array{
		color: #54B1FF;
		font-size: 36rpx;
		position: absolute;
		top: 5rpx;
		right: 56rpx;
	}
</style>
