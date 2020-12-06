<template>
	<view style="">
		<view class="flex-row">
			<view class="formtitle">
				收件人
			</view>
			<input class="uni-input" v-model="sjr" placeholder="请输入收件人" />
		</view>
		<view class="flex-row">
			<view class="formtitle">
				联系号码
			</view>
			<input class="uni-input" v-model="mobile" placeholder="请输入联系号码" />
		</view>
		<view class="flex-row">
			<view class="formtitle">
				邮政编码
			</view>
			<input class="uni-input" v-model="yzbm" placeholder="请输入邮政编码" />
		</view>
		<view class="flex-row flex-between">
			<view class="">
				设为默认地址
			</view>
			<switch @change="switch1Change" />
		</view>
		<view class="" style="border-bottom: 1rpx #ccc solid;">
			<view class="" style="padding: 20rpx;">
				收件地址
			</view>
			<!-- <textarea @blur="bindTextAreaBlur" auto-height placeholder="请输入收件地址" /> -->
			<view class="uni-textarea">
				<textarea @blur="bindTextAreaBlur" placeholder="请输入收件地址" style="padding: 20rpx;background: #fff;width: 100%;" />
				</view>
		</view>
		<button type="primary" @click="addadress" style="width: 80%;margin-top: 40rpx;border-radius:50px">完成</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				sjr:"",//收件人
				mobile:"",//联系号码
				yzbm:"",//邮政编码
			}
		},
		onLoad(options){
			console.log(options)
		},
		methods: {
			onKeyInput(event) {
				this.inputValue = event.target.value
			},
		}
	}
</script>

<style>
page {
		background: #f6f6f6;
	}
	
	.flex-row{
		background: #fff;
		padding: 20rpx 30rpx;border-bottom: 1rpx #ccc solid;
		
	}
	.formtitle{
		width: 240rpx;
	}
</style>
