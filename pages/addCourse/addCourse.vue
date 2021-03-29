<template>
	<view class="addCourse"><!--添加课程模块-->
		<view style="height: 20px;"></view>
		<view class="detailTitle">我要添加</view>
		<view>
			<view class="leftButton" :style="[{backgroundColor:courseTypeActive==1 ? '#9FCFF8' : '#FFFFFF'}]" @click="selectGeneralCourse">通选课</view>
			<view class="rightButton" :style="[{backgroundColor:courseTypeActive==2 ? '#9FCFF8' : '#FFFFFF'}]" @click="selectPECourse">体育课</view>
		</view>

		<view class="detailTitle">课程名称</view>
		<view>
			<input type="text" class="inputBlock" style="width: 83%;margin-left:5%" v-model="courseName" placeholder="输入课程内容" />
		</view>
		
		<view class="detailTitle">授课教师</view>
		<view>
			<input type="text" class="inputBlock" style="width: 83%;margin-left:5%" v-model="courseTeacher" placeholder="输入教师姓名" /><!--绑定数据-->
		</view>
		
		<!--通选-->
		<view v-if="courseTypeActive==1">
			<view class="detailTitle">是否为核心课程？</view>
			<view class="leftButton" :style="[{backgroundColor:coreOrNotActive==1 ? '#9FCFF8' : '#FFFFFF'}]" @click="isCoreCourse">是</view>
			<view class="rightButton" :style="[{backgroundColor:coreOrNotActive==0 ? '#9FCFF8' : '#FFFFFF'}]" @click="notCoreCourse">否</view>	

			<view class="detailTitle">学分类型</view>
			<view class="type1Button" style="border-color:#FFD110; width: 80px" :style="[{backgroundColor:scoreTypeActive==1 ? '#FFD110' : '#FFFFFF'}]" @click="humanity">人文科学</view>
			<view class="type2Button" style="border-color:#FB8D57; width: 80px; background-color:#FDC6AA" :style="[{backgroundColor:scoreTypeActive==2 ? '#FB8D57' : '#FDC6AA'}]" @click="society">社会科学</view>
			<view class="type2Button" style="border-color:##9FCFF8; width: 80px" :style="[{backgroundColor:scoreTypeActive==3 ? '#9FCFF8' : '#FFFFFF'}]" @click="technology">科学技术</view>
			
		</view>
		<!--体育-->
		<view v-if="courseTypeActive==2">
			<view class="detailTitle">授课地点</view>

			<view class="type2Button" :style="[{backgroundColor:addressActive==1 ? '#9FCFF8' : '#FFFFFF'}]" @click="north">北校</view>
			<view class="type2Button" :style="[{backgroundColor:addressActive==2 ? '#9FCFF8' : '#FFFFFF'}]" @click="south">南校</view>
			<view class="type2Button" :style="[{backgroundColor:addressActive==3 ? '#9FCFF8' : '#FFFFFF'}]" @click="internation">国际校区</view>

			<input type="text" class="inputBlock" style="width: 83%;margin-left:5%" placeholder="输入具体地址" v-model="addressDetail"/><!--绑定数据-->
		</view>

		<view class="submitButton" @click="submitNewCourse">提交</view> <!--上传数据-->

	</view>
</template>
<script>
	export default {
		data() {
			return {
				courseName:'',
				courseTeacher:'',
				addressDetail:'',
				
				activeColor:'#9FCFF8',
				inactiveColor:'#FFFFFF',
				
				courseTypeActive:0,
				coreOrNotActive:-1,
				scoreTypeActive:0,
				addressActive:0
			}
		},
		methods: {
			/*还应添加css样式的修改*/
			selectGeneralCourse(){
				this.courseTypeActive=1;
			},
			selectPECourse(){
				this.courseTypeActive=2;
			},
/**/
			isCoreCourse(){
				this.coreOrNotActive=1;
			},
			notCoreCourse(){
				this.coreOrNotActive=0;
			},
/**/
			humanity(){
				this.scoreTypeActive=1;
			},
			society(){
				this.scoreTypeActive=2;
			},
			technology(){
				this.scoreTypeActive=3;
			},
/**/
			north(){
				this.address='北校';
				this.addressActive=1;
			},
			south(){
				this.address='南校';
				this.addressActive=2;
			},
			internation(){
				this.address='国际校区';
				this.addressActive=3;
			},
			submitNewCourse(){
				//提交新课程
				var courseType='';
				if(this.courseTypeActive==1){
					courseType='通选课';
				}
				if(this.courseTypeActive==2){
					courseType='体育课';
				}
				var coreOrNot='';
				if(this.coreOrNotActive==1){
					coreOrNot='是';
				}
				if(this.coreOrNotActive==0){
					coreOrNot='否';
				}
				var scoreType='';
				switch(this.scoreTypeActive){
					case 1:
						scoreType='人文科学';
						break;
					case 2:
						scoreType='社会科学';
						break;
					case 3:
						scoreType='科学技术';
						break;
				}
				var address='';
				switch(this.addressActive){
					case 1:
						address='北校';
						break;
					case 2:
						address='南校';
						break;
					case 3:
						address='国际校区';
						break;
				}
				
				var newCourse;
				//验证
				if(courseType==''){
					uni.showToast({
						title: '请选择课程类型',
						icon:'none',
						duration: 2000
					});
					return;
				}
				if(this.courseName==''){
					uni.showToast({
						title: '请填写课程名称',
						icon:'none',
						duration: 2000
					});
					return;
				}
				if(this.courseTeacher==''){
					uni.showToast({
						title: '请填写教师姓名',
						icon:'none',
						duration: 2000
					});
					return;
				}
				if(this.courseTypeActive==1){
					if(coreOrNot==''){
						uni.showToast({
							title: '请选择是否为核心课程',
							icon:'none',
							duration: 2000
						});
						return;
					}
					if(scoreType==''){
						
						uni.showToast({
							title: '请选择学分类型',
							icon:'none',
							duration: 2000
						});
						return;
					}
					//通选课
					newCourse={
						new_courseType:courseType,
						new_courseName:this.courseName,
						new_courseTeacher:this.courseTeacher,
						new_coreOrNot:coreOrNot,
						new_scoreType:scoreType,
					};
				}
				if(this.courseTypeActive==2){
					if(address==''){
						console.log(newCourse.new_address);
						uni.showToast({
							title: '请选择校区',
							icon:'none',
							duration: 2000
						});
						return;
					}
					if(this.addressDetail==''){
						uni.showToast({
							title: '请填写具体地址',
							icon:'none',
							duration: 2000
						});
						return;
					}
					if(this.addressDetail.length>10){
						uni.showToast({
							title: '地址超过十个字，请重新填写',
							icon:'none',
							duration: 2000
						});
						return;
					}
					//体育课
					newCourse={
						new_courseType:courseType,
						new_courseName:this.courseName,
						new_courseTeacher:this.courseTeacher,
						new_address:address,
						new_addressDetail:this.addressDetail,
					};
				}
				console.log(newCourse);
				//发送数据newCourse信息
				uni.navigateTo({
					url: "/pages/summitRes/summitRes"
				})
			}
		}
	}
</script>
<style>
	@import url("@/static/courseDetail/course_style.css");
</style>
