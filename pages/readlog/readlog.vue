<template>
	<view>
		<view class="title">{{titleList[titleIndex]}}</view>
		
		<!-- 我的收藏 -->
		<view class="item_box" 
					v-for="item in itemList1" :key="item.id"
					:class="titleIndex == 0 ? 'isShow' : ''">
			<list-item :itemDesc="item"/>
		</view>
		
		<!-- 浏览记录 -->
		<view class="item_box" 
					v-for="item in itemList2" :key="item.id" 
					:class="titleIndex == 1 ? 'isShow' : ''">
			<list-item :itemDesc="item"/>
		</view>
		
		<view class="change_container">
			<view class="change_item" 
						v-for="(item, index) in titleList" :key="item.id"
						:class="titleIndex == index ? 'active' : ''"
						@click="changeItem(index)">
				{{item}}
			</view>
		</view>
	</view>
</template>

<script>
	import ListItem from '@/components/listItem/ListItem.vue'
	
	export default {
		data() {
			return {
				titleList: ["我的收藏", "浏览记录"],
				titleIndex: 0,
				itemList1: [
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
				],
				itemList2: [
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
					},
					{
						title: "学校的DNS是什么?",
						classify: ["生活指南", "校园网"]
					}
				]
			}
		},
		components:{
			ListItem,
		},
		methods: {
			changeItem(index){
				this.titleIndex = index;
			}
		}
	}
</script>

<style lang="scss" scoped>
  .title{
		color: black;
		font-size: 52rpx;
		line-height: 88rpx;
		margin: 30rpx 0 0 30rpx;
	}
	
	.change_container{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
		border-radius: 40rpx;
		background-color: #E2F1FD;
		padding: 12rpx 16rpx;
		width: 360rpx;
		height: 48rpx;
		position: fixed;
		// #ifdef H5
		bottom: 130rpx;
		// #endif
		// #ifdef MP-WEIXIN
		bottom: 28rpx;
		// #endif
		left: 174rpx;
		.change_item{
			color: #000;
			border-radius: 28rpx;
			padding: 0 24rpx;
			font-size: 28rpx;
			line-height: 48rpx;
		}
		.active{
			background-color: #9FCFF8;
		}
	}
	
	.isShow{
		display: none;
	}
</style>
