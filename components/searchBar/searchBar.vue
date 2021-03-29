<template>
	<view>
		<view class="input_outer_box">
			<image src="@/static/search/search-button.png" alt="" class="search_icon"/>
			<input type="text" class="input_frame" placeholder="试试搜索关键词吧" v-model="keyWord"/>
			<view class="search-btn" @click="searchClick">搜索</view>
		</view>
		<scroll-view scroll-x="true" class="scroll_box" style="width: 95%;" enable-flex v-if="itemTagList">
			<view v-for="item in itemTagList" class="item_tag" :key="item.id">
				{{item}}
			</view> 
		</scroll-view>
	</view>
</template>

<script>
	export default {
		name:"searchBar",
		data() {
			return {
				keyWord: ""
			};
		},
		props:["itemTagList"],
		mounted(){
			console.log(this.itemTagList)
		},
		methods:{
			searchClick(){
				
				if(this.keyWord != ""){
					this.$emit("searchActive", this.keyWord)
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
  .input_outer_box{
		padding: 28rpx 30rpx 20rpx;
		position: relative;
		.search_icon{
			position: absolute;
			top: 40rpx;
			left: 44rpx;
			width: 38rpx;
			height: 38rpx;
		}
		.input_frame{
			border: 2rpx solid #9FCFF8;
			height: 64rpx;
			border-radius: 32rpx;
			padding-left: 70rpx;
		}
		.search-btn{
			z-index: 9;
			position: absolute;
			background-color: #E2F1FD;
			color: #444;
			padding: 6rpx 20rpx;
			border-radius: 60rpx;
			right: 40rpx;
			top: 35rpx;
		}
	}
	
	.scroll_box{
		height: 50rpx;
		display: flex;
		.item_tag{
			display: inline;
			background: #E2F1FD;
			padding: 6rpx 24rpx 8rpx;
			border-radius: 18rpx;
			color: rgba(0,0,0,1);
			font-size: 22rpx;
			margin-left: 22rpx;
			white-space: nowrap;
		}
	}
	
	
</style>
