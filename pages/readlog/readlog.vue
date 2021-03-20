<template>
	<view class="content">
		<!-- <image class="logo" src="/static/logo.png"></image> -->
		<image class="search" src="../../static/home/searchbar.png"></image>
		<input type="text"
		style="width: 550rpx;height: 80rpx;margin-top: -100rpx;"
		v-model="keyword"
		confirm-type="search"
		@confirm="getSearch"
		placeholder="试试搜索关键词吧"
		placeholder-style="font-size:30rpx;color:#B5B9BF"/>
		<!-- <uni-search-bar @confirm="search" :radius="150" placeholder="试试搜索关键词吧" class="search" placeholder-style="font-size:30rpx;color:#fff" bgColor="#fff"></uni-search-bar> -->
			<view class="keywordbox">
				<view class="keywordblock">
					<view class="keyword" >
						<view v-for="(keyword,index) in keywordList" @tap="doSearch(keyword)" :key='index'>{{keyword}}</view>
					</view>
				</view>
			</view>
		<image class="callus" src="../../static/home/callus.png"></image>
		<!-- <text class="title">{{title}}</text> -->
		<view class="calllight">
			<button plain="true" @click="showCode()">召唤灯灯</button>
		</view>
		<view class="campusE">
			<image src="/static/home/campus.png" ></image>
			<image src="/static/home/helper.png"></image>
		</view>
		<view class="personal">
			<image class="pic" src="/static/home/pic.png"></image>
			<view class="text-welcome">
				<text>Hi,小主人谁谁谁！</text>
			</view>
			<view class="text-service">
				<text>小灯神随时为你服务</text>
			</view>
			<button plain="true">个人中心</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				search:'',
				keyword:'',
				keywordList:[],
			}
		},
		onLoad() {
			this.init();
		},
		methods: {
			init(){
				this.loadKeyword();
			},
			loadKeyword(){
				this.keywordList=['校园网','吃喝玩乐','开网教程','校园网4'];
			},
			//@confirm监听软键盘回车事件
			getSearch(){
			   console.log(this.keyword)
			   uni.showToast({
			      title:this.keyword,
			      duration:2000
			      //icon:"none"
			                
				})
			},
			doSearch(keyword) {
				keyword = keyword===false?this.keyword:keyword;
				this.keyword = keyword;
				uni.showToast({
					title: keyword,
					//icon: 'none',
					
					duration: 10000
			});
			},
			showCode(){
				let con='/static/home/pic.png';
				uni.showModal({
				    title: '确定保存二维码添加灯灯',
				    // content: '这是一个模态弹窗',
					content:con,
					
				    success: function (res) {
				        if (res.confirm) {
							uni.downloadFile({
							        url: '/static/home/pic.png', //仅为示例，并非真实的资源
							        success: function (res) {
							            if (res.statusCode === 200) {
							                console.log('下载成功');
							            }
							        }
							    })
				            console.log('用户点击确定');
				        } else if (res.cancel) {
				            console.log('用户点击取消');
				        }
				    }
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}
	.calllight button {
		height: 50rpx;
		width: 149rpx;
		border-radius: 100rpx;
		border: 0;
		margin-top: -110rpx;
		margin-left: 30rpx;
		margin-right: 480rpx;
		font-size: 25rpx;
		font-weight: 800;
		color:rgba(255,255,255,0.1);
		text-align: center;
		line-height: 1.7;
	}
	.campusE {
		width:650rpx;
		justify-content: space-between;
		flex-direction: row;
	}
	.campusE image{
		width:325rpx;
		height: 200rpx;
		
	}
	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}
	.search {
		height:80rpx;
		width:700rpx;
		z-index: -1;
		margin-top: 20rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 20rpx;
	}	
	.callus {
		height:400rpx;
		width:650rpx;
		margin-top: 1rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 20rpx;
	}
	.calllight {
		
	}
	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
	.keyword {
		width:750rpx;
	}
	.keywordbox {
		width: 650rpx;
		height:auto;
		border-radius:20upx 20upx 0 0;
		background-color:#fff;
	}
	.keywordbox.keywordblock {
		flex-direction: row;
		padding:10upx 0;
	}
	.keywordbox .keywordblock .keyword {
		white-space: nowrap;
		width:94%;
		padding:3px 3%;
		display:flex;
		flex-flow:wrap;
		justify-content:flex-start;
		flex-direction: row;
	}
	.keywordbox .keywordblock .keyword>view {
		display:flex;
		justify-content:center;
		align-items:center;
		border-radius:60upx;
		padding:0 20upx;
		margin:10upx 20upx 10upx 0;
		height:60upx;
		font-size:20upx;
		background-color:rgb(242,242,242);
		color:#6b6b6b;
	}
	.personal {
		width: 98%;
		height: 230rpx;
		margin-top: 30rpx;
		background-color: #fcfcfc;
		box-shadow: 0rpx -10rpx 10rpx #e2e2e2;
		border-radius: 10rpx;
	}
	.personal button{
		border-radius: 50rpx;
		width: 160rpx;
		height: 50rpx;
		font-size: 26rpx;
		border: 0;
		color: #fff;
		background-color: #E0F3FF;
		margin-top: -220rpx;
		margin-right: 50rpx;
		line-height: 1.8;
	}
	.pic{
		width: 110rpx;
		height: 110rpx;
		border-radius: 20rpx;
		margin-top: 20rpx;
		margin-left: 50rpx;
	}
	.text-welcome{
		width: 650rpx; 
		height: 50rpx;
		align-content: flex-start;
		margin-top: 10rpx;
		margin-left: 50rpx;
		font-size: 50rpx;
		font-weight: 500;
	}
	.text-service {
		width: 650rpx;
		height: 50rpx;
		align-content: flex-start;
		margin-top: 10rpx;
		margin-left: 50rpx;
		font-weight: 400;
	}
</style>
