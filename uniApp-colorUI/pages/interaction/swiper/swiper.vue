<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>轮播图</view>
		</cu-custom>
		<view class="cu-bar bg-white">
			<view class="action">
				<text class="cuIcon-title text-pink"></text> 全屏限高轮播
			</view>
			<view class="action">
				<switch class="sm" @change="dotStyle" />
			</view>
		</view>
		<swiper class="screen-swiper" :class="swiperStyle?'square-dot':'round-dot'" :indicator-dots="true" :circular="true"
		 :autoplay="true" interval="5000" duration="500">
			<swiper-item v-for="(item, index) in swiperList" v-key='index'>
				<image :src="item.url" mode="aspectFill" v-if="item.type == 'image'"></image>
				<video :src="item.url" v-if="item.type == 'video'" autoplay loop muted show-play-btn="false" controls="false"
				 objectFit="cover"></video>
			</swiper-item>
		</swiper>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-pink"></text> 卡片式轮播
			</view>
		</view>
		<swiper class="card-swiper" :class="swiperStyle?'square-dot':'round-dot'" :indicator-dots="true" :circular="true"
		 :autoplay="true" :interval="5000" :duration="500" indicator-color="#8799a3" indicator-active-color="#0081ff" @change="cardSwiper">
			<swiper-item v-for="(item, index) in swiperList" v-key='index'>
				<view class="swiper-item" :class="cardCur == index ? 'cur':''">
					<image :src="item.url" mode="aspectFill" v-if="item.type == 'image'"></image>
					<video :src="item.url" v-if="item.type == 'video'" autoplay loop muted show-play-btn="false" controls="false"
					 objectFit="cover"></video>
				</view>
			</swiper-item>
		</swiper>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-pink"></text> 堆叠式轮播
			</view>
		</view>
		<view class="tower-swiper" @touchmove="towerMove" @touchstart="towerStartFn" @touchend="towerEnd">
			<view class="tower-item" :class="item.zIndex == 1 ? 'none' : ''" v-for="(item, index) in swiperList" v-key='index'
			 :style="{'--index': item.zIndex, '--left': item.mLeft}">
				<view class="swiper-item">
					<image :src="item.url" mode="aspectFill" v-if="item.type == 'image'"></image>
					<video :src="item.url" v-if="item.type == 'video'" autoplay loop muted show-play-btn="false" controls="false"
					 objectFit="cover"></video>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swiperStyle: false,
				swiperList: [{
					id: 0,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big84000.jpg'
				}, {
					id: 1,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big84001.jpg',
				}, {
					id: 2,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big39000.jpg'
				}, {
					id: 3,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big10001.jpg'
				}, {
					id: 4,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big25011.jpg'
				}, {
					id: 5,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big21016.jpg'
				}, {
					id: 6,
					type: 'image',
					url: 'https://ossweb-img.qq.com/images/lol/web201310/skin/big99008.jpg'
				}],
				cardCur: 0,
				towerStart: 0,
				direction: ''
			}
		},
		created() {
			let that = this
			that.towerSwiper(that.swiperList)
		},
		methods: {
			dotStyle(e) {
				let that = this
				that.swiperStyle = e.detail.value
			},
			cardSwiper(e) {
				let that = this
				that.cardCur = e.detail.current
			},
			// 初始化堆叠式轮播图
			towerSwiper(dataList) {
				let that = this
				let list = dataList
				for (let i = 0; i < list.length; i++) {
					list[i].zIndex = parseInt(list.length / 2) + 1 - Math.abs(i - parseInt(list.length / 2))
					list[i].mLeft = i - parseInt(list.length / 2)
				}
				that.swiperList = list
				console.log(that.swiperList)
			},
			// towerSwiper触摸开始
			towerStartFn(e) {
				let that = this
				that.towerStart = e.touches[0].pageX
			},
			// towerSwiper计算方向
			towerMove(e) {
				let that = this
				that.direction = e.touches[0].pageX - that.towerStart > 0 ? 'right' : 'left'
			},
			// towerSwiper计算滚动
			towerEnd(e) {
				let that = this
				let direction = that.direction
				let list = that.swiperList
				if (direction == 'right') {
					let mLeft = list[0].mLeft;
					let zIndex = list[0].zIndex;
					for (let i = 1; i < list.length; i++) {
						list[i - 1].mLeft = list[i].mLeft
						list[i - 1].zIndex = list[i].zIndex
					}
					list[list.length - 1].mLeft = mLeft;
					list[list.length - 1].zIndex = zIndex;
					that.swiperList = list;
				} else {
					let mLeft = list[list.length - 1].mLeft;
					let zIndex = list[list.length - 1].zIndex;
					for (let i = list.length - 1; i > 0; i--) {
						list[i].mLeft = list[i - 1].mLeft
						list[i].zIndex = list[i - 1].zIndex
					}
					list[0].mLeft = mLeft;
					list[0].zIndex = zIndex;
					that.swiperList = list;
				}
			}
		}
	}
</script>

<style>
	.tower-swiper .tower-item {
		transform: scale(calc(0.5 + var(--index) / 10));
		margin-left: calc(var(--left) * 100rpx - 150rpx);
		z-index: var(--index);
	}
</style>
