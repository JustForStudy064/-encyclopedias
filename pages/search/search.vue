<template>
	<view>
		<search-bar :itemTagList="itemTagList" @searchActive="searchActive"></search-bar>
		<view class="search_title">{{title_text}}</view>
		<!-- 列表信息显示 -->
		<view class="item_box" v-for="item in itemList" v-show="!noFound">
			<list-item :itemDesc="item"/>
		</view>
		<!-- 找不到页面显示 -->
		<no-result v-show="noFound"/>
		<!-- 底部信息显示 -->
		<bottom-info v-show="noFound"/>
	</view>
</template>

<script>
	import BottomInfo from './childCpns/BottomInfo.vue'
	
	import searchBar from '@/components/searchBar/searchBar.vue'
	import ListItem from '@/components/listItem/ListItem.vue'
	import NoResult from '@/components/noResult/NoResult.vue'

	export default {
		data() {
			return {
				itemTagList: ["校园网", "校园网", "校园网", "吃喝玩乐", "开网的流程"],
				// 根据情况
				title_text: "热门百科",
				itemList: [
					{
						item_id: "1",
						title: "学校的DNS是什么?",
						classify: ["生活指南", "校园网"]
					},
					{
						item_id: "2",
						title: "怎样缴空调费和水电费",
						classify: ["生活指南", "宿舍须知"]
					},
					{
						item_id: "3",
						title: "志愿时如何录入",
						classify: ["学习助手", "志愿时"]
					},
					{
						item_id: "4",
						title: "华南理工大学接受面试攻读研究生测试测试",
						classify: ["学习助手", "学分考试"]
					},
					{
						item_id: "5",
						title: "华南理工大学入网指南",
						classify: ["学习助手", "学分考试"]
					}
				],
				noFound: false
			}
		},
		components:{
			ListItem,
			BottomInfo,
			NoResult,
			searchBar
		},
		methods: {
			searchActive(keyWord){
				let word = keyWord == "" ? "请输入关键词" : "搜索的关键词为:" + keyWord
				uni.showToast({
					title: word + ";可以输入 ces 试试效果",
					icon:'none',
					duration: 2000
				});
				if(keyWord == "ces"){
					this.noFound = true
				}else{
					this.noFound = false
				}
			}
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
