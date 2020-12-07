<template>
	<view>
		<view class="input_outer_box">
			<image src="@/static/search/search-button.png" alt="" class="search_icon"/>
			<input type="text" class="input_frame" placeholder="试试搜索关键词吧"/>
		</view>
		<scroll-view scroll-x="true" class="scroll_box" style="width: 95%;" enable-flex>
			<item-tag v-for="item in itemTagList" :itemTagText="item" class="item_tag"/>
		</scroll-view>
		<view class="search_title">{{title_text}}</view>
		<!-- 列表信息显示 -->
		<view class="item_box" v-for="item in itemList" >
			<list-item :itemDesc="item"/>
		</view> 
		<!-- 底部信息显示 -->
		<bottom-info/>
		<!-- 找不到页面显示 -->
		<no-result/>
	</view>
</template>

<script>
	import ItemTag from './childCpns/ItemTag.vue'
	import ListItem from './childCpns/ListItem.vue'
	import BottomInfo from './childCpns/BottomInfo.vue'
	import NoResult from './childCpns/NoResult.vue'
	
	export default {
		data() {
			return {
				itemTagList: ["校园网", "校园网", "校园网", "吃喝玩乐", "开网的流程"],
				// 根据情况
				title_text: "热门百科",
				itemList: [
					{
						title: "学校的DNS是什么?",
						classify: ["生活指南", "校园网"]
					},
					{
						title: "怎样缴空调费和水电费",
						classify: ["生活指南", "宿舍须知"]
					},
					{
						title: "志愿时如何录入",
						classify: ["学习助手", "志愿时"]
					},
					{
						title: "华南理工大学接受面试攻读研究生测试测试",
						classify: ["学习助手", "学分考试"]
					},
					{
						title: "华南理工大学入网指南",
						classify: ["学习助手", "学分考试"]
					}
				]
			}
		},
		components:{
			ItemTag,
			ListItem,
			BottomInfo,
			NoResult
		},
		methods: {
			
		}
	}
</script>

<style scoped>
  .input_outer_box{
		padding: 28rpx 30rpx 20rpx;
		position: relative;
	}
	
	.input_frame{
		border: 2rpx solid #9FCFF8;
		height: 64rpx;
		border-radius: 32rpx;
		padding-left: 70rpx;
	}
	
	.search_icon{
		position: absolute;
		top: 40rpx;
		left: 44rpx;
		width: 38rpx;
		height: 38rpx;
	}
	
	.scroll_box{
		height: 50rpx;
		display: flex;
	}
	
	.item_tag{
		display: inline;
		height: 80rpx;
		width: 200rpx;
	}
	
	.search_title{
		color: rgba(0,0,0,1);
		font-size: 52rpx;
		padding: 50rpx 0 0 54rpx; 
	}
</style>
