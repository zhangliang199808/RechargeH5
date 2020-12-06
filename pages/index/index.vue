<template>
	<view class="content">
		<!-- <view data-v-d8da5c7c="" class="banner" style="width: 100%;"> -->
			<img  mode="aspectFit" src="../../static/img/homebanner.jpg" style="width: 100%;height: 100%;"> 
			<!---->
			<!-- </view> -->
		<!-- <container style="width:100%"> -->
		<!-- <ls-swiper :list="base_lsit" imgKey="imgUrl" :loop="true" :dots='true' :autoplay='true' style="width:100%" @clickItem="clickItem()" /> -->
		<!-- </container> -->
		<!-- <textscroll :list="list"/> -->
		<uni-notice-bar showIcon="true" scrollable="true" text="[多行] 这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏这是 NoticeBar 通告栏，这是 NoticeBar 通告栏，这是 NoticeBar 通告栏"></uni-notice-bar>

		<!-- <image class="logo" src="/static/logo.png"></image>
		<view class="text-area">
			<text class="title">{{title}}</text>
		</view> -->
		<view class="toplist">
			<view class="list" @click="listtpye(index)" v-for="(item,index) in topList" :key="index">
				<image src="" mode="" style="display:block;width:90rpx;height:90rpx;background:#ccc;margin:0 auto"></image>
				<view class="listtext">
					{{item.name}}
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import uniNoticeBar from '@/components/uni-notice-bar/uni-notice-bar.vue'
	import lsSwiper from '../../components/ls-swiper/index.vue'
	export default {
		components: {
			lsSwiper,
			uniNoticeBar,
		},
		data() {
			return {
				list: ['1分钟前，无夏购买了会员', '2分钟前，无夏购买了会员', '3分钟前，无夏购买了会员'],
				base_lsit: [{
						// name: '1',
						imgUrl: 'https://picb.zhimg.com/80/v2-3f5c7bdcc228d3798a044b78023459d3_720w.jpg?source=1940ef5c',
					},
					{
						// name: '2',
						imgUrl: 'https://pic3.zhimg.com/80/v2-1deed0eca463f87f36d6e88363ae2693_720w.jpg?source=1940ef5c',
					},
					{
						// name: '3',
						imgUrl: 'https://picb.zhimg.com/80/v2-520f230f8cb8a0943b8582dcd77ec6ba_720w.jpg',
					},
					{
						// name: '4',
						imgUrl: 'https://pic1.zhimg.com/80/v2-33e85bdfafbb4aa52ce6f70f319dbb4f_720w.jpg',
					},
				], //轮播图
				topList: [{
						name: '供热缴费',
					},
					{
						name: "水电燃气"
					},
					{
						name: "投诉报修"
					},
					{
						name: "卡号管理"
					},
					{
						name: "电子发票"
					},
					{
						name: "收费标准"
					},
					{
						name: "网点地图"
					},
					{
						name: "业务办理"
					},
					// {name:"电子发票"},
					// {name:"电子发票"},
				],
			}
		},
		onLoad() {

		},
		methods: {
			//点击列表跳转页面
		listtpye(id){
			console.log(id)
			if(id==0){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			if(id==1){uni.navigateTo({
			    url: '/pages/gas/gas'
			});}
			if(id==2){uni.navigateTo({
			    url: '/pages/repair/repair'
			});}
			if(id==3){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			if(id==4){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			if(id==5){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			if(id==6){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			if(id==7){uni.navigateTo({
			    url: '/pages/heating/heating'
			});}
			console.log(12)
			// uni.navigateTo({
			//     url: '/pages/heating/heating'
			// });
		},
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

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}

	.toplist {
		display: flex;
		flex-wrap: wrap
	}

	.list {
		width: 25%;
		margin: 20rpx 0
	}

	.listtext {
		text-align: center;
		font-size: 20rpx;
		margin-top: 10rpx
	}
</style>
