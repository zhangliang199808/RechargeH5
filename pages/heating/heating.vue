<template>
	<view>
		<ul data-v-6416d0a4="" class="weui-cells appeal-links" style="margin-top: 6px;">
			<!---->
			<li data-v-6416d0a4="" class="weui-cell weui-cell_access">
				<div data-v-6416d0a4="" class="weui-cell__bd">
					<p data-v-6416d0a4="">全部</p>
				</div>
				<div data-v-6416d0a4="" class="weui-cell__ft"></div>
			</li>
		</ul>
		<view class="bd" @click="addcard">
			还没有绑定卡号，请添加
		</view>
		 <button type="primary"  @click="addcard" class="addbutton">+添加</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			}
		},
		methods: {
			addcard(){
				uni.navigateTo({
				    url: '/pages/heating/addcard/addcard'
				});
			},
		}
	}
</script>

<style >
	page {
		background: #f6f6f6;
	}

	.weui-cells {
		padding: 0;
	}

	.weui-cells li {
		display: flex;
		background: #FFF;
		/* border-top:1rpx solid #d9d9d9; */
		/* border-bottom:1rpx solid #d9d9d9; */
		justify-content: flex-end;
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

	.bd {
		background: #fff;
		height: 200rpx;
		text-align: center;
		line-height: 200rpx;
		margin: 40rpx 30rpx;
		color: #999;
	}
	.addbutton{
		position: fixed;
		bottom: 0;
		width: 100%;
	}
</style>
