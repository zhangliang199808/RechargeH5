<template>
	<view style="">
		
		<view class="" style="">
			<view class="" style="padding: 20rpx;">
				留言标题
			</view>
			<input class="uni-input" v-model="title" placeholder="请输入收件人" style="background: #fff;padding: 20rpx;"/>
			<!-- <textarea @blur="bindTextAreaBlur" auto-height placeholder="请输入收件地址" /> -->
			<!-- <view class="uni-textarea">
				<textarea @blur="bindTextAreaBlur" placeholder="请在此输入标题..." style="padding: 20rpx;background: #fff;width: 100%;" />
				</view> -->
		</view>
		<view class="" style="">
			<view class="" style="padding: 20rpx;">
				留言内容
			</view>
			<!-- <textarea @blur="bindTextAreaBlur" auto-height placeholder="请输入收件地址" /> -->
			<view class="uni-textarea">
				<textarea @blur="bindTextAreaBlur" v-model="content" placeholder="请在此输入留言内容..." style="padding: 20rpx;background: #fff;width: 100%;" />
				</view>
		</view>
		<button type="primary" @click="addadress" style="width: 80%;margin-top: 40rpx;border-radius:50px">提交</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
title:"",
content:"",
			}
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
		padding: 20rpx 30rpx;
		/*  sborder-bottom: 1rpx #ccc solid; */
		
	}
	.formtitle{
		width: 240rpx;
	}
</style>
