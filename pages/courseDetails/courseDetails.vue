<template>
	<view>
		<!-- <view style="height: 20px;"></view> -->
		<view class="briefIntro" style="height:100px">
		<!--获取当前课程的id、标题、类型等信息-->
			<view class="introCourseTitle" :style="{borderLeftColor: courseActiveColor}">{{courseName}}</view>
			<view style="clear: both"></view>
			<view style="margin-left:27px;margin-top:8px;">
				<view style="float: left;">
					<view class="introCourseDetail">
						<span v-if="courseType==='通选课'" style="color:#888888">类别</span><!--通选-->
						<span v-if="courseType==='体育课'">地点</span> <!--体育-->
						<span style="margin-left: 5px;" :style="{color:courseActiveColor}"> {{ course_type_Or_address}}</span><!--后台数据输出，根据类别修改颜色-->
					</view>
					<view style="clear: both"></view>
					<view class="introCourseDetail">
						<span style="color:#888888">教师</span>
						<span style="margin-left: 5px;">{{ teacherName }}</span><!--后台数据输出-->
					</view>
				</view>
			<!--加上图标，点击收藏变色，点赞变色，评论跳转-->
			<!-- <view style="margin-right:18px;margin-left:55%">
				<view>
					<image id="markIcon" src="@/static/course/mark_active.png" class="icon" style="margin-left: 12px;"></image>
					<image id="likeIcom" src="@/static/course/like_active.png" class="icon" style="margin-left: 15px;"></image>
					<image id="commentIcon" src="@/static/course/comment.png" class="icon" style="margin-left: 20px;"></image>
				</view>
				<view>
					<span class="funcButton" :style="[{color: mark==true ? '#F0CA2C' : '#BFBFBF'}]" @click="toMark">收藏</span>
					<span class="funcButton" :style="[{color: like==true ? '#27B2FF' : '#BFBFBF'}]" @click="toLike">赞({{like_total_num}})</span>
					<span class="funcButton">评论({{ commentList.length}})</span>
				</view>
			</view> -->
			<view class="icon_container">
				<view class="icon_item" :style="[{color: mark==true ? '#F0CA2C' : '#BFBFBF'}]" @click="toMark">
					<image src="@/static/course/mark_active.png" :style=""></image>
					<view>收藏</view>
				</view>
				<view class="icon_item" :style="[{color: like==true ? '#27B2FF' : '#BFBFBF'}]" @click="toLike">
					<image src="@/static/course/like_active.png" style="padding:0 24rpx;"></image>
					<view>点赞({{like_total_num}})</view>
				</view>
				<view class="icon_item">
					<image src="@/static/course/comment.png" style="padding:0 22rpx;"></image>
					<view>评论({{commentNum}})</view>
				</view>
			</view>
		</view>
		</view>
		
		<view class="courseComment" v-for="(item,idx) in commentList">
			<view class="commentContent">{{item.content}}</view><!--输出后台读取的数据-->
			<view class="contentDetail">考勤<text style="color:#000000;margin-left: 5px;"> {{item.checkFreq}}</text></view>
			<view class="contentDetail">考核<text style="color:#000000;margin-left: 5px;"> {{item.examWay}}</text></view>
			<view class="contentDetail">给分<text style="color:#000000;margin-left: 5px;"> {{item.score}}</text></view>
			<view class="commentDateAndLike">
				<text>{{item.date}} </text>
				<view class="good-box">
					<image src="@/static/course/like_active.png" class="good-img"></image>
					<text :style="[{color: commentList[idx].likeThisComment==true ? '#27B2FF' : '#BFBFBF'}]" @click="toLikeThisComment(idx)">赞同<text>({{item.like_num}})</text></text><!--读取后台数据-->
				</view>
			</view>
		</view>
		<!-- <view class="submitButton" @click="goComment">我要评论</view> -->
		<view class="submit-button" @click="goComment">我要评论</view>
		<view style="height:160rpx;"></view>
	</view>
</template>

<script>
	export default {
		// onLoad(option){
		// 	this.id=option.id;
		// 	this.courseName=option.courseName;
		// 	this.courseType=option.courseType;
		// 	this.course_type_Or_address=option.course_type_Or_address;
		// 	this.teacherName=option.teacherName;
		// 	this.commentList=JSON.parse(decodeURIComponent(option.commentList));
			
		// 	this.mark=JSON.parse(option.mark);
		// 	this.like=JSON.parse(option.like);

		// 	this.like_total_num=option.like_total_num;
		// 	if(this.course_type_Or_address=="人文科学"){
		// 		this.courseActiveColor='#FFD110';
		// 	}
		// 	else if(this.course_type_Or_address=="社会科学"){
		// 		this.courseActiveColor='#FB8D57';
		// 	}
		// 	else if(this.course_type_Or_address=="科学技术"){
		// 		this.courseActiveColor='#9FCFF8';
		// 	}
		// 	else this.courseActiveColor='#27B2FF';
		// },
		data() {
			return {
				id:'0001',
				courseName:'英美音乐与文化',
				courseType:'通选课',/*通选课/体育课*/
				course_type_Or_address:'人文',/*通选课：人文/社会/科学；体育课：地点*/
				courseActiveColor:'#FFD110',
				teacherName:'陈艳艳',
				commentList:[
						{	
							content: "老师很好！",
							checkFreq: "从不考勤",
							examWay: "期末开卷考试",
							score: "90分以上",
							date: "2018-01-01",
							like_num: 165
						},
						{	
							content: "老师很好。",
							checkFreq: "偶尔考勤",
							examWay: "期末闭卷考试",
							score: "85分以上",
							date: "2018-01-02",
							like_num: 100
						},
						{	content: "老师很好。",
							checkFreq: "偶尔考勤",
							examWay: "期末闭卷考试",
							score: "85分以上",
							date: "2018-01-02",
							like_num: 100
						},
						{	content: "老师很好。",
							checkFreq: "偶尔考勤",
							examWay: "期末闭卷考试",
							score: "85分以上",
							date: "2018-01-02",
							like_num: 100
						},
						{	content: "老师很好。",
							checkFreq: "偶尔考勤",
							examWay: "期末闭卷考试",
							score: "85分以上",
							date: "2018-01-02",
							like_num: 100
						}
				],
				mark:'10',
				like:'100',
				like_total_num:'20',
				commentNum: "100",
			}
		},
		methods: {
			toMark(){
				this.mark = !this.mark;
			},
			toLike(){
				if(this.like==false){
					this.like_total_num++;
				}
				else if(this.like==true){
					this.like_total_num--;
				}
				this.like = !this.like;
				
			},
			goComment(){
				uni.navigateTo({
					url:'../addComment/addComment?id=' + this.id
					+'&courseName=' + this.courseName
					+'&courseType=' + this.courseType
					+'&course_type_Or_address=' + this.course_type_Or_address
					+'&teacherName=' + this.teacherName
				})
			},
			toLikeThisComment(idx){
				if(this.commentList[idx].likeThisComment==false){
					this.commentList[idx].like_num++;
				}
				else if(this.commentList[idx].likeThisComment==true){
					this.commentList[idx].like_num--;
				}
				this.commentList[idx].likeThisComment = !this.commentList[idx].likeThisComment;
				}
		}
	}
</script>

<style>
</style>

<style lang='scss' scoped>
	/* @import url("../course_style.css"); */
	@import url("@/static/courseDetail/course_style.css");
	.icon_container{
		display: flex;
		flex-direction: row;
		flex-wrap: nowrap;
		font-size: 22rpx;
		float: right;
		width: 400rpx;
		justify-content: space-around;
		text-align: center;
		.icon_item{
			display: flex;
			flex-direction: column;
			justify-content: center;
			image{
				width: 50rpx;
				height: 50rpx;
			}
		}
	}
	
	.submit-button{
		position: fixed;
		bottom: 40rpx;
		margin: 0 72rpx;
		padding: 16rpx 230rpx;
		font-size: 34rpx;
		color: #FFFFFF;
		background-color: #9FCFF8;
		line-height: 58rpx;
		text-align: center;
		border-radius: 40rpx;
	}
	
	
	.good-box{
		float:right;
		display: flex;
		line-height: 48rpx;
		.good-img{
			width: 44rpx;
			height: 44rpx;
		}
	}
</style>
