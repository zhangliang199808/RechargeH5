<template>
	<view>
		<view v-if="!showList" class="" style="text-align: center;margin-top: 80rpx;">
			<view class="12" style="">
				<img src="../../static/img/none.png" mode="" style="display:block;width:400rpx;margin: auto;" />
			</view>
			<view class="" style="margin-top: 20rpx;color: #ccc;">
				您还没有添加收货地址哦～

			</view>
		</view>
		<!-- 列表 暂时内容未知 -->
		<view v-if="showList" class="list">
			<view class="card" v-for="(item,index) in addadresslist" :key="index">
				<view class="cardtop">
					<view class="flex-row">
						<view class="" style="font-size:36rpx;margin-right: 20rpx;">
							{{item.name}}
						</view>
						<view class="" style="line-height: 46rpx;">
							{{item.phone}}
						</view>
					</view>
					<view class="" style="word-break:break-all;">
						{{item.adress}}
					</view>
				</view>
				<view class="cardbottom flex-row flex-between">
					<view class="">
						<radio-group @change="radioChange">
							<label class="uni-list-cell uni-list-cell-pd">
								<view>
									<radio style="transform:scale(0.7)" :value="item.moren" :checked="item.id === current" />默认地址
								</view>
							</label>
						</radio-group>
					</view>
					<view class="flex-row">
						<view class="" @click="edit(item.id)" style="margin-right: 20rpx;">
							编辑
						</view>
						<view class="">
							删除
						</view>
					</view>
				</view>
			</view>
		</view>
		<button type="primary" @click="addadress" style="width: 80%;margin-top: 40rpx;border-radius:50px">+新增地址</button>
	</view>
</template>


<script>
	export default {
		data() {
			return {
				showList: false,
				addadresslist: [{
					name: "名字",
					id: 1,
					adress: "新城区dhfadhfkjadfagdlfadsljfgadjshfgakjdsgfajkdsgfjasdgfakjsh",
					phone: "12345678900",
					check: false,
					moren: "第一条"
				}, {
					name: "名字",
					id: 2,
					adress: "新城区海欣家园二单元一楼1205",
					phone: "12345678900",
					check: true,
					moren: "第二条"
				}],
				current: 0
			}
		},
		methods: {
			addadress() {
				uni.navigateTo({
					url: '/pages/shdz/addshdz/addshdz'
				})
			},
			radioChange(evt) {
				var _this = this
				for (let i = 0; i < _this.addadresslist.length; i++) {
					if (_this.addadresslist[i].value === evt.target.value) {
						_this.current = _this.addadresslist[i].id;
						break;
					}
				}
			},
			edit(id){
				uni.navigateTo({
					url: '/pages/shdz/addshdz/addshdz?id='+id
				});
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

	.card {
		background: #fff;
		padding: 10rpx 25rpx;
		margin-bottom: 20rpx;
	}

	.cardtop {
		border-bottom: 1rpx #ccc solid;
		padding: 10rpx 0;
	}

	.cardbottom {
		margin: 10rpx 0;
	}
</style>
