<template>
	<view class="item-tag" :style="{width:itemlength + 'rpx'}">
		{{itemTagText}}
	</view>
</template>

<script>
	export default {
		name: "ItemTag",
		props: ["itemTagText"],
		data(){
			return {
				itemlength: 0
			}
		},
		created(){
      this.$data.itemlength = this.$props.itemTagText.length * 22
		},
	}
</script>

<style scoped>
	.item-tag{
		background: #E2F1FD;
		padding: 6rpx 24rpx 8rpx;
		border-radius: 18rpx;
		color: rgba(0,0,0,1);
		font-size: 22rpx;
		margin-left: 22rpx;
	}
</style>
