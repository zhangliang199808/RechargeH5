<template>
	<view>
		<view v-if="!showData" class="none">
			暂无数据
		</view>
		<view v-if="showData" class="none">
			暂无数据
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				showData:false
			}
		},
		methods: {
			
		}
	}
</script>

<style>
	page{
		background: #f6f6f6;
	}
.none{
	padding:20rpx;
	text-align: center;
	background: #fff;
}
</style>
