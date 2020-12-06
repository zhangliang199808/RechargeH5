<template>
	<view>
		<ls-swiper :list="base_lsit" imgKey="imgUrl" :loop="true" :dots='true' :autoplay='true' style="width:100%" @clickItem="clickItem()" />
		<ul data-v-6416d0a4="" class="weui-cells appeal-links" style="margin-top: 20rpx;">
			<!---->
			<li data-v-6416d0a4="" class="weui-cell weui-cell_access">
				<div data-v-6416d0a4="" class="weui-cell__bd">
					<p data-v-6416d0a4="">全部</p>
				</div>
				<div data-v-6416d0a4="" class="weui-cell__ft"></div>
			</li>
		</ul>
	
	</view>
</template>

<script>
	import lsSwiper from '../../components/ls-swiper/index.vue'
	export default {
		components: {
			lsSwiper,
		},
		data() {
			return {
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
				], 
			}
		},
		methods: {
			
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
</style>
