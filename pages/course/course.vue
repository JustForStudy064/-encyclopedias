<template>
	<view>
		<search-bar></search-bar>
		<!-- 废弃的原始下拉菜单 -->
		<!-- <view class="item_box_container">
			<view class="dropdown" v-for="(item1, index1) in filterList" :key="item.id">
				<view class="dropbtn" @click="tagClick(index1)">{{item1.state}}</view>
				<view class="dropdown-content" :class="activeIndex == index1 ? 'active' : ''" >
					<text v-for="(item2, index2) in item1.detailList" :key="item2.id"
								@click="itemClick(index1, index2)">{{item2}}</text>
				</view>
			</view>
			<view>添加课程</view>
		</view> -->
		<!-- 引用第三方下拉菜单 -->
		<slFilter :themeColor="themeColor" :menuList="menuList" independence></slFilter>
		<view v-for="item in itemObj" :key="item.id">
			<courseItem :itemObj="item"></courseItem>
		</view>
		<view class="add-lesson" @click="addClick()">
			<image src="@/static/collect/add-btn.png"></image>
		</view>
	</view>
</template>

<script>
	import searchBar from "@/components/searchBar/searchBar.vue"
	import slFilter from "@/components/sl-filter/sl-filter.vue"
	import courseItem from "./childCpns/courseItem.vue"
	
	export default {
		data() {
			return {
				// filterList:[
				// 	{
				// 		state: "通选课",
				// 		detailList: ["全部", "人文科学", "社会科学", "科学技术", "核心"]
				// 	},
				// 	{
				// 		state: "体育课",
				// 		detailList: ["南校", "北校", "国际校区"]
				// 	}
				// ],
				activeIndex: -1,
				tagIndex1: "",
				tagIndex2: "",
				menuList: [
					{
						"title": "课程类型",
						"isMutiple": true,
						"key": "key_1",
						"detailList": [
							{
								"title": "不限",
								"value": "不限",
							},
							{
								"title": "人文科学",
								"value": "人文科学",
							},
							{
								"title": "社会科学",
								"value": "社会科学",
							},
							{
								"title": "科学技术",
								"value": "科学技术",
							},{
								"title": "人文科学·核心",
								"value": "人文科学·核心",
							},
							{
								"title": "社会科学·核心",
								"value": "社会科学·核心",
							},
							{
								"title": "科学技术·核心",
								"value": "科学技术·核心",
							},
							{
								"title": "体育课",
								"value": "体育课",
							}
						]
					},
					{
						"title": "校区",
						"isMutiple": true,
						"key": "key_1",
						"detailList": [
							{
								"title": "不限",
								"value": "不限",
							},
							{
								"title": "南校",
								"value": "南校",
							},
							{
								"title": "北校",
								"value": "北校",
							},
							{
								"title": "国际校区",
								"value": "国际校区",
							}
						]
					}
				],
				itemObj:[{
					course_id: "0002",
					type_id: "1",
					title: "生涯规划与求职技巧",
					teacher: "吴耀华",
					type_text: "社会科学·核心",
					type_color: "#FB8D57",
					is_good: false,
					good_num: "100",
					comment_num: "40",
				},{
					course_id: "0003",
					type_id: "1",
					title: "大学生心理健康",
					teacher: "巢老师",
					type_text: "社会科学",
					is_good: false,
					type_color: "#54B1FF",
					good_num: "100",
					comment_num: "70",
				},{
					course_id: "0001",
					type_id: "2",
					title: "英美音乐与文化	",
					teacher: "陈艳艳",
					type_text: "人文科学·核心",
					type_color: "#FFD110",
					good_num: "100",
					comment_num: "100",
				},{
					course_id: "0004",
					type_id: "2",
					title: "生涯规划与求职技巧",
					teacher: "吴耀华",
					type_text: "社会科学·核心",
					type_color: "#FB8D57",
					good_num: "100",
					comment_num: "100",
				},{
					course_id: "0005",
					type_id: "1",
					title: "大学生心理健康",
					teacher: "巢老师",
					type_text: "社会科学",
					type_color: "#54B1FF",
					good_num: "100",
					comment_num: "100",
				},{
					course_id: "0005",
					type_id: "2",
					title: "英美音乐与文化	",
					teacher: "陈艳艳",
					type_text: "人文科学·核心",
					type_color: "#FFD110",
					good_num: "165",
					comment_num: "100",
				},{
					course_id: "0006",
					type_id: "1",
					title: "大学生心理健康",
					teacher: "巢老师",
					type_text: "社会科学",
					type_color: "#54B1FF",
					good_num: "165",
					comment_num: "100",
				},{
					course_id: "0007",
					type_id: "2",
					title: "英美音乐与文化	",
					teacher: "陈艳艳",
					type_text: "人文科学·核心",
					type_color: "#FFD110",
					good_num: "165",
					comment_num: "100",
				},{
					course_id: "0008",
					type_id: "3",
					title: "英美音乐与文化	",
					teacher: "陈艳艳",
					type_text: "人文科学·核心",
					type_color: "#FFD110",
					good_num: "165",
					comment_num: "100",
				}],
				themeColor: "#54B1FF"
			}
		},
		components:{
			searchBar,
			slFilter,
			courseItem
		},
		methods: {
			tagClick(index){
				this.activeIndex = this.activeIndex == index ? -1 : index
			},
			itemClick(index1, index2){
				if(index1 == 0){
					this.tagIndex1 = index1 + '-' + index2
					this.filterList[0].state = this.filterList[0].detailList[index2]
				}else{
					this.tagIndex2 = index1 + '-' + index2
					this.filterList[1].state = this.filterList[1].detailList[index2]
				}
				console.log(this.tagIndex1 , this.tagIndex2)
				this.tagClick(index1)
			},
			addClick(){
				uni.navigateTo({
					url: "/pages/addCourse/addCourse",
					success: ()=> console.log("OK!"),
					fail: (err) => console.log(err)
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.item_box_container{
		display: flex;
		flex-direction: row;
		justify-content: space-around;
	}
	
	/* 设置下拉按钮的样式 */
	.dropbtn {
		font-size: 16px;
		border: none;
		cursor: pointer;
	}

	.dropdown {
		position: relative;
		display: inline-block;
	}

	/* 下拉内容（默认隐藏） */
	.dropdown-content {
		display: none;
		position: absolute;
		text-align: center;
		min-width: 128rpx;
		font-size: 26rpx;
		box-shadow: 0px 8px 16px 0px rgba(0,0,0,0.2);
		z-index: 1;
	}

	/* 下拉链接 */
	.dropdown-content text {
		color: black;
		padding: 12px 16px;
		text-decoration: none;
		display: block;
	}
	
	.active{
		display: block;
	}
	
	.add-lesson{
		position: fixed;
		// #ifdef H5
		bottom: 140rpx;
		// #endif
		// #ifdef MP-WEIXIN
		bottom: 80rpx;
		// #endif
		right: 30rpx;
		image{
			width: 100rpx;
			height: 100rpx;
		}
	}

</style>
