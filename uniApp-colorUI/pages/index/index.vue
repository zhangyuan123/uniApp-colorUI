<template>

	<view class="content">
		<image src="/static/BasicsBg.png" mode='widthFix' class='png' style='width:100%;height:486rpx'></image>
		<view class="navList">
			<navigator class="navItem" :class="'bg-' + item.color" :url="'/pages/basic/' + item.name + '/' + item.name" v-for="(item, index) in elements" :key='index'>
				<view class="navItemTitle">{{item.title}}</view>
				<view class="navItemName">{{item.name}}</view>
				<text :class="'cuIcon-' + item.icon"></text>
			</navigator>
		</view>

		<!-- #ifdef APP-PLUS -->
		<!-- <text>app</text> -->
		<!-- #endif -->
		<!-- #ifdef MP-WEIXIN -->
		<!-- <text>MP-WEIXIN</text> -->
		<!-- #endif -->

	</view>
</template>

<script>
	export default {
		data() {
			return {
				elements: [{
						title: '布局',
						name: 'layout',
						color: 'cyan',
						icon: 'newsfill'
					},
					{
						title: '背景',
						name: 'background',
						color: 'blue',
						icon: 'colorlens'
					},
					{
						title: '文本',
						name: 'text',
						color: 'purple',
						icon: 'font'
					},
					{
						title: '图标 ',
						name: 'icon',
						color: 'mauve',
						icon: 'icon'
					},
					{
						title: '按钮',
						name: 'button',
						color: 'pink',
						icon: 'btn'
					},
					{
						title: '标签',
						name: 'tag',
						color: 'brown',
						icon: 'tagfill'
					},
					{
						title: '头像',
						name: 'avatar',
						color: 'red',
						icon: 'myfill'
					},
					{
						title: '进度条',
						name: 'progress',
						color: 'orange',
						icon: 'icloading'
					},
					{
						title: '边框阴影',
						name: 'shadow',
						color: 'olive',
						icon: 'copy'
					},
					{
						title: '加载',
						name: 'loading',
						color: 'green',
						icon: 'loading2'
					},
				],
			}
		},
		onLoad() {
			console.log('onload');
		},
		methods: {

		}
	}
</script>

<style>
	.navList {
		width: 100%;
		padding: 0 40rpx;
		display: flex;
		justify-content: space-between;
		flex-wrap: wrap;
	}

	.navItem {
		height: 180rpx;
		padding: 30rpx;
		border-radius: 12rpx;
		width: 45%;
		margin: 0 2.5% 40rpx;
		background-image: url(https://image.weilanwl.com/color2.0/cardBg.png);
		background-size: cover;
		background-position: center;
		position: relative;
		z-index: 1;
	}

	.navItem::after {
		content: "";
		position: absolute;
		z-index: -1;
		background-color: inherit;
		width: 100%;
		height: 100%;
		left: 0;
		bottom: -10%;
		border-radius: 10rpx;
		opacity: 0.2;
		transform: scale(0.9, 0.9);
	}

	.navItemTitle {
		font-size: 32rpx;
		font-weight: 300;
	}

	.navItemTitle::first-letter {
		font-size: 40rpx;
		margin-right: 4rpx;
	}

	.navItemName {
		font-size: 28rpx;
		text-transform: capitalize;
		margin-top: 20rpx;
		position: relative;
	}

	.navItemName::before {
		content: "";
		position: absolute;
		display: block;
		width: 40rpx;
		height: 6rpx;
		background: #fff;
		bottom: 0;
		right: 0;
		opacity: 0.5;
	}

	.navItemName::after {
		content: "";
		position: absolute;
		display: block;
		width: 100rpx;
		height: 1px;
		background: #fff;
		bottom: 0;
		right: 40rpx;
		opacity: 0.3;
	}

	.navItemName::first-letter {
		font-size: 36rpx;
		font-weight: bold;
		margin-right: 2rpx;
	}

	.navItem text {
		position: absolute;
		right: 30rpx;
		top: 30rpx;
		font-size: 52rpx;
		width: 60rpx;
		height: 60rpx;
		text-align: center;
		line-height: 60rpx;
	}
</style>
