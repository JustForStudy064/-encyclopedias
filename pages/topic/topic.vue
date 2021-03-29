<template>
	<view>
		<image src="@/static/search/search-button.png" class="search-btn" @click="toSearch"></image>
		<view class="container" v-for="item1 in gradeList">
			<view class="title">
				{{item1.title}}
			</view>
			<view class="item" v-for="item2 in item1.gradeItem"
						 open-type="switchTab"
						 @click="itemClick(item2)">
				<image :src="item2.icon" mode="widthFix"></image>
				<text class="text-name">{{item2.name}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				gradeList: [
					{
						title: '生活指南',
						gradeItem: [
							{
								index: "0-0",
								icon:'../../static/campusEncyclopedia/wifi.png',
								name:'校园网'
							},
							{
								index: "0-1",
								icon:'../../static/campusEncyclopedia/facilities.png',
								name:'校园设施'
							},
							{
								index: "0-2",
								icon:'../../static/campusEncyclopedia/dormitory.png',
								name:'宿舍须知'
							},
							{
								index: "0-3",
								icon:'../../static/campusEncyclopedia/card.png',
								name:'一卡通'
							},
							{
								index: "0-4",
								icon:'../../static/campusEncyclopedia/clothes.png',
								name:'衣食住行'
							}
						]
					},
					{
						title: '学分助手',
						gradeItem: [
							{
								index: "1-0",
								icon:'../../static/campusEncyclopedia/volunteer.png',
								name:'志愿时'
							},
							{
								index: "1-1",
								icon:'../../static/campusEncyclopedia/bonus.png',
								name:'奖助学金'
							},
							{
								index: "1-2",
								icon:'../../static/campusEncyclopedia/exam.png',
								name:'学分考试'
							},
						]
					},
					{
						title: '学校介绍',
						gradeItem: [
							{
								index: "2-0",
								icon:'../../static/campusEncyclopedia/telephone.png',
								name:'常用网站与账号电话'
							},
							{
								index: "2-1",
								icon:'../../static/campusEncyclopedia/college.png',
								name:'学院介绍'
							},
							{
								index: "2-2",
								icon:'../../static/campusEncyclopedia/major.png',
								name:'专业介绍'
							},
							{
								index: "2-3",
								icon:'../../static/campusEncyclopedia/department.png',
								name:'社团与部门介绍'
							},
						]
					}
				]
			}
		},
		methods: {
			itemClick(item){
				uni.navigateTo({
					url: "../topicDetail/topicDetail?" + "itemIndex=" + item.index + "&itemName=" + item.name,
					success: ()=> console.log("success"),
					fail: (err)=> console.log(err)
				})
				console.log(item.index)
			},
			toSearch(){
				uni.navigateTo({
					url: "/pages/search/search"
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.container {
		padding: 20rpx 40rpx;
	}
	.title {
		font-size: 56rpx;
		font-weight: 400;
		border-bottom: 4rpx solid #f2f2f2;
	}
	.item {
		height: 65rpx;
		display: flex;
		align-items: center;
	}
	.text-name {
		margin-left: 10rpx;
	}
	image {
		width: 40rpx;
	}
	
	/* 新增内容 */
	.search-btn{
		height: 40rpx;
		width: 40rpx;
		position: absolute;
		right: 50rpx;
		top: 40rpx;
	}
</style>
