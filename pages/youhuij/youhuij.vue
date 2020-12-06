<template>
	<view>
		<view v-if="!showList" class="" style="text-align: center;margin-top: 80rpx;">
			<view class="12" style="">
				<img src="../../static/img/none.png" mode="" style="display:block;width:400rpx;margin: auto;" />
			</view>
			<view class="" style="margin-top: 20rpx;color: #ccc;">
				竟然一张优惠卷都没有

			</view>
		</view>
		<!-- 列表 暂时内容未知 -->
		<view v-if="showList" class="list">

		</view>
		<!-- <button type="primary" @click="addadress" style="width: 80%;margin-top: 40rpx;border-radius:50px">+新建留言</button> -->
	</view>
</template>


<script>
	export default {
		data() {
			return {
				showList: false
			}
		},
		methods: {
			addadress() {
				uni.navigateTo({
					url: '/pages/liuYan/addliu/addliu'
				})
			},
		}
	}
</script>

<style>
	page {
		background: #f6f6f6;
	}

	.weui-cells {
		padding: 0;
	}

	.weui-cells li {
		display: flex;
		background: #FFF;
		border-top: 1rpx solid #d9d9d9;
		border-bottom: 1rpx solid #d9d9d9;
		justify-content: space-between;
		transform-origin: 0 100%;
		transform-origin: 0 0;
	}

	.weui-cell {
		font-family: Microsoft YaHei;
		line-height: 1.41176471;
		font-size: 16px;
		margin: 0;
		box-sizing: border-box;
		list-style: none;
		padding: 10px 15px;
		position: relative;
		display: flex;
		-webkit-box-align: center;
		align-items: center;
		-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
		color: inherit;
	}

	.weui-cell_access .weui-cell__ft:after {
		content: " ";
		display: inline-block;
		height: 6px;
		width: 6px;
		border-width: 2px 2px 0 0;
		border-color: #c8c8cd;
		border-style: solid;
		-webkit-transform: matrix(.71, .71, -.71, .71, 0, 0);
		transform: matrix(.71, .71, -.71, .71, 0, 0);
		position: relative;
		top: -2px;
		position: absolute;
		top: 50%;
		margin-top: -4px;
		right: 2px;
	}

	.weui-cell_access .weui-cell__ft {
		padding-right: 13px;
		position: relative;
	}
</style>
