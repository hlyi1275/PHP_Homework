<template>
	<view class="content">
		<view class="width95 title">{{title}}</view>
		
		<!-- 轮播图 -->
		<view class="banner-image">
			<!-- <image class="banner-image" src="static/banner.png"></image> -->
			<u-swiper :list="imgList" height="220" mode="dot" border-radius="20" ></u-swiper>
		</view>  
		
		<!-- 搜索框 -->
		<navigator class="width95" url="search">
			<view> 
				<input class="input"  placeholder="输入店铺" placeholder-style="color:#b8b8b8" /> 
			</view>
		</navigator>
		
		<!-- 选项 -->
		<view class="width95">
			<view class="width40 d-row d-jc-between">
				<view :class="{active: activeTabIndex == index}"
					v-for="(item,index) in activeList" :key="index" @tap="handleTab(index)">
					<view class="title-name">{{ item.title }}</view>
					<view :class="{titleBottom: activeTabIndex == index}" ></view>
				</view>
			</view>
		</view>
		
		<!-- 店铺 -->
		<view class="width90 d-row d-jc-around" style="margin-top: 30rpx;height: 180rpx;"
			v-for="(item,index) in sList" :key="index" @tap="intoDetails(item)">
			<view class="s-head d-clo d-jc-centen d-ai-centen "><image class="s-head-img" :src="item.headImg"></image></view>
			<view class="s-detail d-clo d-jc-around">
				<view class="font-bold font32">{{item.name}}</view>
				<view class="font28 gray3">月销{{item.yx}}</view>
				<view class="d-row d-jc-between gray3">
					<view>起送 ¥{{item.qs}} | 配送 ¥{{item.ps}}</view>
					<view>{{item.sj}}分钟 {{item.jl}}m</view>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: '中午好,午饭时间到了!',
				activeList: [
					{title: '距离最近', value: 'distance'},
					{title: '销量最高', value: 'sales'},
				],
				activeTabIndex: '',
				imgList: [{
						image: '/static/banner.png',
						title: '蒹葭苍苍，白露为霜。所谓伊人，在水一方'
					},
					{
						image: '/static/banner.png',
						title: '蒹葭萋萋，白露未晞。所谓伊人，在水之湄'
					},
					{
						image: '/static/banner.png',
						title: '蒹葭萋萋，白露未晞。所谓伊人，在水之湄'
					},
					{
						image: '/static/banner.png',
						title: '蒹葭萋萋，白露未晞。所谓伊人，在水之湄'
					}
				],
				sList:[
					{
						id:'1',
						headImg:'/static/logo.png',
						name:'百果园',
						yx:'123',
						qs:'20',
						ps:'4',
						sj:'40',
						jl:'800'
					},
					{
						id:'2',
						headImg:'/static/logo.png',
						name:'百果园',
						yx:'123',
						qs:'20',
						ps:'4',
						sj:'40',
						jl:'800'
					},
					{
						id:'3',
						headImg:'/static/logo.png',
						name:'百果园',
						yx:'123',
						qs:'20',
						ps:'4',
						sj:'40',
						jl:'800'
					}
				]
			}
		},
		onLoad() {
			this.activeTabIndex = 0
		},
		watch: {
			// watch 监听器,监听到数据发生变化时执行
			activeTabIndex: async function(val) {
				const type = this.activeList[val].value
				await this.getIndexList(type)
			}
		},
		methods: {
			handleTab(index) {
				this.activeTabIndex = index
			},
			async getIndexList(type){
				console.log("获取"+type+"数据列表")
			},
			intoDetails(item){
				uni.navigateTo({
					url:'../store/index?id='+item.id+'&name='+item.name+"&headImg="+item.headImg,
					animationType: 'pop-in',
					animationDuration: 2000
				})
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
	}
	.title{
		font-size: 30rpx;
		font-weight: bold;
		margin-top: 10rpx;
	}
	.banner-image{
		margin-top: 20rpx;
		margin-bottom: 20rpx;
		width: 95%;
		border-radius:0 0 50rpx 50rpx;
	}
	.input{
		background-color: #f7f7f7;
		border-radius: 10rpx;
		padding: 20rpx;
	}
	
	.title-name{
		padding: 15rpx 0;
	}
	.active {
		font-weight: bold;
		color: #007AFF;
	}
	.titleBottom{
		margin: 0 auto;
		width: 60%;
		border-bottom: 5rpx solid #007AFF;
	}
	
	.s-head{
		flex: 1;
	}
	.s-head-img{
		width: 120rpx;
		height: 120rpx;
		border-radius: 50%;
	}
	.s-detail{
		flex: 3;
	}
</style>
