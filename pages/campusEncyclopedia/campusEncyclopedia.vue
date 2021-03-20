<!-- <template>
	<view class="container" v-for="item1 in gradeList">
		<view class="title">
			{{item1.title}}
		</view>
		
		<navigator class="item" v-for="item2 in item1.gradeItem">
			<image :src="item2.icon" mode="widthFix"></image>
			<text class="text-name">{{item2.name}}</text>
		</navigator>
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
								icon:'../../static/campusEncyclopedia/wifi.png',
								name:'校园网'
							},
							{
								icon:'../../static/campusEncyclopedia/facilities.png',
								name:'校园设施'
							},
							{
								icon:'../../static/campusEncyclopedia/dormitory.png',
								name:'宿舍须知'
							},
							{
								icon:'../../static/campusEncyclopedia/card.png',
								name:'一卡通'
							},
							{
								icon:'../../static/campusEncyclopedia/clothes.png',
								name:'衣食住行'
							}
						]
					},
					{
						title: '学分助手',
						gradeItem: [
							{
								icon:'../../static/campusEncyclopedia/volunteer.png',
								name:'志愿时'
							},
							{
								icon:'../../static/campusEncyclopedia/bonus.png',
								name:'奖助学金'
							},
							{
								icon:'../../static/campusEncyclopedia/exam.png',
								name:'学分考试'
							},
						]
					},
					{
						title: '学校介绍',
						gradeItem: [
							{
								icon:'../../static/campusEncyclopedia/telephone.png',
								name:'常用网站与账号电话'
							},
							{
								icon:'../../static/campusEncyclopedia/college.png',
								name:'学院介绍'
							},
							{
								icon:'../../static/campusEncyclopedia/major.png',
								name:'专业介绍'
							},
							{
								icon:'../../static/campusEncyclopedia/department.png',
								name:'社团与部门介绍'
							},
						]
					}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>
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
</style>
 -->