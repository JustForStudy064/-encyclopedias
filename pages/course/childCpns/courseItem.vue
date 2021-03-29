<template>
	<view>
		<view class="title" @click="courseClick()">
			
			<!-- h5生效，小程序不生效的写法 -->
			<!-- <view class="title-text" :style="titleStyle">{{itemObj.title}}
				<image src="@/static/collect/orange_arrow.png" class="arrow-pic"></image>
			</view> 
			 -->
			 <!-- h5、 小程序均生效的写法 -->
			<view class="title-text" :style="{'border-color': itemObj.type_color}">{{itemObj.title}}
				<image src="@/static/collect/orange_arrow.png" class="arrow-pic"></image>
			</view>
			
			<view class="teacher-text">教师: <text>{{itemObj.teacher}}</text></view>
			<view class="type-text">
				<view>类别: <text :style="{color: itemObj.type_color}">{{itemObj.type_text}}</text></view>
				<view class="tag-container">
					<view class="tag-item">
						<image src="@/static/collect/comment.png" class="com-pic"></image>
						<view class="com_text" :style="{color: itemObj.type_color}">{{itemObj.comment_num}}</view>
					</view>
					<view class="tag-item">
						<image src="@/static/collect/good.png" class="com-pic" style="height:40rpx;"></image>
						<view class="com_text" :style="{color: itemObj.type_color}">{{itemObj.good_num}}</view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default{
		// props:["title"]
		data(){
			return {
				// itemObj:{
				// 	title: "英美音乐与文化	",
				// 	teacher: "陈艳艳",
				// 	type_text: "社会科学",
				// 	type_color: "#FB8D57",
				// 	good_num: "165",
				// 	comment_num: "30",
				// }
			}
		},
		props:["itemObj"],
		computed:{
			titleStyle(){
				return {
					"color": this.itemObj.type_color,
					"border-left": "8rpx solid " + this.itemObj.type_color
				}
			}
		},
		methods:{
			courseClick(){
				console.log("courseClick")
				uni.navigateTo({
					url: "/pages/courseDetails/courseDetails?" + "course_id=" + this.itemObj.course_id,
					success: ()=> console.log("OK!"),
					fail: (err) => console.log(err)
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.title{
		font-size: 34rpx;
		font-weight: 300;
		padding: 12rpx 0;
		margin-left: 54rpx;
		border-bottom: 2rpx solid rgba(0,0,0,.05);
		.title-text{
			border-left: 8rpx solid;
			text-indent: 8rpx;
		}
		
		.arrow-pic{
			padding: 12rpx 58rpx 0 0;
			width: 14rpx;
			height: 26rpx;
			float: right;
		}
		
		.teacher-text, .type-text{
			font-size: 26rpx;
			color: #888;
			text-indent: 22rpx;
			font-weight: 300;
			margin-top: 12rpx;
			text{
				color: #000;
			}
		}
		
		.type-text{
			display: flex;
			flex-direction: row;
			justify-content: space-between;
		}
	
		.com-pic{
			width: 44rpx;
			height: 44rpx;
		}
		
		.com_text{
			line-height: 44rpx;
			font-size: 22rpx;
			color: orange
		}
	}
	
	.tag-container{
		display: flex;
		width: 300rpx;
		justify-content: space-around;
		flex-direction: row;
		.tag-item{
			display: flex;
		}
	}
	
	
</style>
