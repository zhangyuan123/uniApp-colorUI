<template>
	<scroll-view scroll-y class="scrollPage">
		<cu-custom bgImage='https://image.weilanwl.com/color2.0/plugin/cjkz2329.jpg'>
			<view slot='content'>
				<image src="../../static/cjkz.png" mode="widthFix"></image>
			</view>
		</cu-custom>
		<view class="cu-card">
			<view class="cu-item bg-img shadow-blur" v-for="(item, index) in list" v-key :style="{backgroundImage: ' url('+item.img +')'}" @click="toChild" :data-url='item.url'>
				<view class="cardTitle">{{item.title}}</view>
			</view>
		</view>
	</scroll-view>
</template>

<script>
	export default {
		data() {
			return {
				list: [{
						title: '索引列表',
						img: 'https://image.weilanwl.com/color2.0/plugin/sylb2244.jpg',
						url: '/indexes/indexes'
					},
					{
						title: '微动画',
						img: 'https://image.weilanwl.com/color2.0/plugin/wdh2236.jpg',
						url: '/animation/animation'
					},
					{
						title: '全屏抽屉',
						img: 'https://image.weilanwl.com/color2.0/plugin/qpct2148.jpg',
						url: '/drawer/drawer'
					},
					{
						title: '垂直导航',
						img: 'https://image.weilanwl.com/color2.0/plugin/qpczdh2307.jpg',
						url: '/verticalnav/verticalnav'
					}
				]
			}
		},
		methods: {
			toChild(e) {
				let that = this
				let url = e.currentTarget.dataset.url
				uni.navigateTo({
					url: '/pages/plugin' + url
				})
			}
		}
	}
</script>

<style>
	.cardTitle {
		color: #fff;
		padding: 90rpx 60rpx;
		font-size: 40rpx;
		font-weight: 300;
		transform: skew(-10deg, 0deg);
		position: relative;
		text-shadow: 0px 0px 6rpx rgba(0, 0, 0, 0.3)
	}

	.cardTitle::before {
		content: "";
		position: absolute;
		width: 60rpx;
		height: 6rpx;
		border-radius: 20rpx;
		background-color: #fff;
		display: block;
		top: 60rpx;
		left: 50rpx;
		transform: skew(10deg, 0deg);
	}

	.cardTitle::after {
		content: "";
		position: absolute;
		width: 140rpx;
		border-radius: 6rpx;
		height: 24rpx;
		background-color: #fff;
		display: block;
		bottom: 76rpx;
		left: 90rpx;
		transform: skew(10deg, 0deg);
		opacity: 0.1;
	}
</style>
