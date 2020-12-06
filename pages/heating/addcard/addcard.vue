<template>
	<view>
		<!-- <view type="primary" @click="btnClick">选择地址</view> -->
		<ul data-v-6416d0a4="" class="weui-cells appeal-links" style="margin: 40rpx 0;">
			<!---->
			<li data-v-6416d0a4="" @click="btnClick" class="weui-cell weui-cell_access">
				<div data-v-6416d0a4="" class="weui-cell__bd">
					<p data-v-6416d0a4="" style="color:#999">{{city}}</p>
				</div>
				<div data-v-6416d0a4="" class="weui-cell__ft"></div>
			</li>
		</ul>
		<selectAddress ref='selectAddress' @selectAddress="successSelectAddress"></selectAddress>
		<view class="flex">
			<view class="" style="white-space: nowrap;  padding-right: 30px;">
				选择分组
			</view>
			<axb-check-box ref="radio3" :list="sartTime" @change="radioChangeType" style="  "></axb-check-box>
		</view>
		<view class="flex">
			<view class="" style="white-space: nowrap;  padding-right: 30px;">
				请输入
			</view>
			<input class="uni-input" @input="onKeyInput" placeholder="输入同步到view中" />
			<!-- <axb-check-box ref="radio3" :list="sartTime" @change="radioChangeType" style="  "></axb-check-box> -->
		</view>
		<button type="primary"  @click="addcard"  class="addbutton">+添加</button>
	</view>
</template>

<script>
	import axbCheckBox from '@/components/axb-checkbox/axb-checkbox.vue'
	import selectAddress from '@/components/yixuan-selectAddress/yixuan-selectAddress.vue'
	export default {
		components: {
			selectAddress,
			axbCheckBox
		},
		data() {
			return {
				city: "选择地址",
				inputValue: '',
				sartTime: [{ // 开始日期
					name: '我家',
					value: '1',
					checked: 0
				}, {
					name: '朋友',
					value: '2',
					checked: 0
				}, {
					name: '父母',
					value: '3',
					checked: 0
				}, {
					name: '房东',
					value: '4',
					checked: 0
				}],
			}
		},
		methods: {
			btnClick() {
				this.$refs.selectAddress.show()
			},
			successSelectAddress(address) { //选择成功回调
				console.log(address)
				this.city = address
			},
			radioChangeType(val) {
				console.log(val) // 单选时 返回选中项的value, 反选返回null
			},
			onKeyInput(event) {
				this.inputValue = event.target.value
				console.log(this.inputValue)
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

	.flex {
		display: flex;
		background: #fff;
		/* flex-wrap: wrap; */
		padding: 40rpx 30rpx;
		/* margin-top: 30rpx; */
		border-bottom: 1rpx #e5e5e5 solid;
	}
	.addbutton{margin-top: 40rpx;
	width: 80%;}
</style>
