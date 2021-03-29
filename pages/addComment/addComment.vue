<template>
	<view>
		<!-- <view style="height: 20px;"></view> -->
		<view class="briefIntro">
			<view class="courseTitle" :style="{borderLeftColor: courseActiveColor}">{{courseName}}</view><!--课程名称。此处标题样式与之前不同-->
			<view style="float:left">
				
				<view class="introCourseDetail">
					<text v-if="courseType=='通选课'">
						<text style="color:#888888">类别</text>
					</text>
					<text v-if="courseType=='体育课'">
						<text style="color:#888888">地点</text>
					</text>
					<text style="margin-left: 5px" :style="{color: courseActiveColor}">{{course_type_Or_address}}</text>
				</view>
				<view class="introCourseDetail" style="clear:both">
					<text style="color:#888888">教师</text>
					<text style="margin-left: 5px;">{{teacherName}}</text>
				</view>
			</view>
		</view>
		<view class="toComment">
			<view v-if="courseType=='通选课'"><!--通选-->
				<view v-for="(item1, idx) in courseCom_tx">
					<view class="detailTitle">{{ item1.title}}</view>
					<view v-for="(item2, index) in item1.option">
						<view v-if="idx===0 || idx===2" class="type2Button" :style="[{backgroundColor:tx_active_KaoqinAndKaohe[idx][index] ? '#9FCFF8' : '#FFFFFF'}]" @click="select_kaoqinANDkaohe(index, idx)">{{ item2.str}}</view>
						<view v-if="idx===1" class="type2Button" :style="[{backgroundColor:tx_active_checkFreq==index ? '#9FCFF8' : '#FFFFFF'}]" @click="select_kaoqin(index)">{{ item2.str}}</view>
					</view>
					<input type="text" class="inputBlock" style="width: 22%;margin-left:5%" placeholder="其他..." />
				</view>	
			</view>
			
			<view v-if="courseType=='体育课'"><!--体育-->
				<view v-for="item3 in courseCom_ty">
					<view class="detailTitle">{{ item3.title}}</view>
					<view v-for="(item4, index) in item3.option">
						<view class="type2Button" :style="[{backgroundColor:ty_active_Kaohe[index] ? '#9FCFF8' : '#FFFFFF'}]" @click="select_kaohe(index)">{{ item4.str}}</view>
					</view>
					<input type="text" class="inputBlock" style="width: 83%;margin-left:5%" placeholder="详细讲讲你们的考核方式吧~" /><!--绑定数据-->
				</view>
			</view>
			
			<view class="detailTitle">期末成绩</view>
			<view v-for="(item5, index) in scoreRange">
				<view class="type2Button"  :style="[{backgroundColor:active_score==index ? '#9FCFF8' : '#FFFFFF'}]" @click="select_qimo(index)">{{ item5.str}}</view>
			</view>
			<view class="detailTitle">我还想说更多</view>
			<textarea type="text" class="inputBlock" style="
					width: 83%;
					margin-left:5%;
					border-radius: 5px; 
					border: 1px solid #707070;
					height: 129px;
					<!-- letter-spacing: 59px; -->
					" v-model="moreDetails"/><!--不少于10字，不多于100字-->  <!--文字未靠首行-->
			<view class="submitButton" @click="submitComment">我填好啦</view> <!--上传数据-->
		</view>
	</view>
</template>

<script>
	export default {
		onLoad(option){
			this.id=option.id;
			this.courseName=option.courseName;
			this.courseType=option.courseType;
			this.course_type_Or_address=option.course_type_Or_address;
			this.teacherName=option.teacherName;
			if(this.course_type_Or_address=="人文科学"){
				this.courseActiveColor='#FFD110';
			}
			else if(this.course_type_Or_address=="社会科学"){
				this.courseActiveColor='#FB8D57';
			}
			else if(this.course_type_Or_address=="科学技术"){
				this.courseActiveColor='#9FCFF8';
			}
			else this.courseActiveColor='#27B2FF';
		},
		data() {
			return {
				courseActiveColor:'',
				courseName:'',
				courseType:'',/*1:通选课 2:体育课*/
				course_type_Or_address:'test',/*通选课：人文/社会/科学；体育课：地点*/
				teacherName:'',
				finalScore:'',
				moreDetails:'',
				tx_active_KaoqinAndKaohe:[
					[false,false,false,false,false],
					[false,false,false,false,false],//这一行没意义
					[false,false,false,false,false]//通选课考核
				],
				tx_active_checkFreq: -1,
				ty_active_Kaohe:[false,false,false],//体育课考核（多选）
				active_score: -1,
				courseCom_tx:[
					{
						title:'考勤方式',
						option:[
							{ str:'全员点名'},
							{ str:'扫码签到'},
							{ str:'抽人答题'},
							{ str:'随堂作业'},
							{ str:'不考勤'},
						]
					},
					{
						title:'考勤频率',
						option:[
							{ str:'每节课'},
							{ str:'经常'},
							{ str:'偶尔'},
							{ str:'从不'},
							{ str:'随机'},
						]
					},
					{
						title:'考核方式',
						option:[
							{ str:'闭卷考'},
							{ str:'开卷考'},
							{ str:'小组作业'},
							{ str:'pre展示'},
							{ str:'论文'},
						]
					}
				],
				courseCom_ty:[
					{
						title:'考核方式',
						option:[
							{ str:'体能测试'},
							{ str:'慕课'},
							{ str:'笔试'},
						]
					}
				],
				scoreRange:[
						{ str:'90以上'},
						{ str:'86-90'},
						{ str:'80-85'},
						{ str:'70-80'},
						{ str:'60-70'},
						{ str:'60以下'}
				],
			}
		},
		methods: {
			//通选
			select_kaoqinANDkaohe(index,idx){//考勤方式、考核方式
				var temp = this.tx_active_KaoqinAndKaohe[idx];
				this.$set(temp,index,!temp[index]);
			},
			select_kaoqin(index){//考勤频率
				this.tx_active_checkFreq = index;
			},
			//体育
			select_kaohe(index){
				var temp = this.ty_active_Kaohe;
				this.$set(temp,index,!temp[index]);
			},
			
			select_qimo(index){
				this.active_score = index;
			},
			submitComment(){
				try{
					//上传数据
					var examWay=[];
					var tx_checkWay=[];
					var newComment;
					if(this.courseType=='通选课'){
						for(var i=0;i<this.tx_active_KaoqinAndKaohe[0].length;i++){
							if(this.tx_active_KaoqinAndKaohe[0][i]==true){
								tx_checkWay.push(this.courseCom_tx[0].option[i].str);
							}
						}
						for(var i=0;i<this.tx_active_KaoqinAndKaohe[2].length;i++){
							if(this.tx_active_KaoqinAndKaohe[2][i]==true){
								examWay.push(this.courseCom_tx[2].option[i].str);
							}
						}
						newComment={
							new_id:this.id,
							new_tx_checkWay:tx_checkWay,//考勤方式，多选
							new_tx_checkFreq:this.courseCom_tx[1].option[this.tx_active_checkFreq].str,//考勤频率，单选
							
							new_examWay:examWay,//考核方式，多选
							new_finalScore:this.scoreRange[this.active_score].str//期末成绩，单选
						};
					}
					if(this.courseType=='体育课'){
						for(var i=0;i<this.ty_active_Kaohe.length;i++){
							if(this.ty_active_Kaohe[i]==true){
								examWay.push(this.courseCom_ty[0].option[i].str);
							}
						}
						newComment={
							new_id:this.id,
							new_examWay:examWay,//考核方式，多选
							new_finalScore:this.scoreRange[this.active_score].str//期末成绩，单选
						};
					}
					
					uni.navigateTo({
						url: "/pages/summitRes/summitRes",
						success: ()=>console.log("跳转到提交成功界面"),
						fail: (err)=>console.log(err)
					})
				}catch(e){
					uni.showToast({
						title: '小主人还没有填写完全哦～',
						icon:'none',
						duration: 2000
					});
				}
				
				
				console.log(newComment);
				
				//上传newComment对象
			}
			
		}
	}
</script>

<style>
	@import url("@/static/courseDetail/course_style.css");
</style>
