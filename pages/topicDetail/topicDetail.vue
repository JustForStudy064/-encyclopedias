<template>
	<view>
		<view class="title">{{itemName}}</view>
		
		<view class="item_box" v-for="item in itemList" :key="item.id">
			<list-item :itemDesc="item"/>
		</view>
	</view>
</template>

<script>
	import ListItem from "@/components/listItem/ListItem.vue"
	
	export default{
		onLoad: function (option) { //option为object类型，会序列化上个页面传递的参数
			console.log(option.itemIndex); //打印出上个页面传递的参数。
			console.log(option.itemName); //打印出上个页面传递的参数。
			this.itemName = option.itemName;
		},
		components:{
			ListItem
		},
		data(){
			return {
				itemName: "",
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
		
	}
</script>

<style lang="scss" scoped>
	.title{
		font-size: 52rpx;
		line-height: 88rpx;
		margin-left: 32rpx;
		font-weight: 300;
		color: #000;
	}
	
	.item_box{
		
	}
	
</style>
