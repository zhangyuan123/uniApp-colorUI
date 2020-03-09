<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>导航栏</view>
		</cu-custom>
		<view class="bg-grey text-center padding margin" v-for="(item, index) in 10" v-key='index' v-if="index == tabCur">Tab{{index}}</view>
		<view class="bg-white">
			<view class="cu-bar">
				<view class="action">
					<text class="cuIcon-titles text-orange"></text> 默认
				</view>
			</view>
			<scroll-view scroll-x class='nav' scroll-with-animation scroll-left="scrollLeft">
				<view class="cu-item" :class="index == tabCur ? 'text-green cur' : ''" v-for="(item, index) in 10" v-key='index' :data-id='index' @click="tabSelect">Tab{{index}}</view>
			</scroll-view>
		</view>
		<view class="bg-white margin-top">
			<view class="cu-bar">
				<view class="action">
					<text class="cuIcon-title text-orange"></text> 居中
				</view>
			</view>
			<scroll-view scroll-x class='nav text-center' scroll-with-animation scroll-left="scrollLeft">
				<view class="cu-item" :class="index == tabCur ? 'text-blue cur' : ''" v-for="(item, index) in 3" v-key='index' :data-id='index' @click="tabSelect">Tab{{index}}</view>
			</scroll-view>
		</view>
		<view class="bg-white margin-top">
			<view class="cu-bar">
				<view class="action">
					<text class="cuIcon-title text-orange"></text> 平分
				</view>
			</view>
			<scroll-view scroll-x class='nav' scroll-with-animation scroll-left="scrollLeft">
				<view class="flex text-center">
					<view class="cu-item flex-sub" :class="index == tabCur ? 'text-orange cur' : ''" v-for="(item, index) in 4" v-key='index' :data-id='index' @click="tabSelect">Tab{{index}}</view>
				</view>
			</scroll-view>
		</view>
		<view class="bg-white margin-top">
			<view class="cu-bar">
				<view class="action">
					<text class="cuIcon-title text-orange"></text> 背景
				</view>
			</view>
			<scroll-view scroll-x class='nav text-center bg-red' scroll-with-animation scroll-left="scrollLeft">
				<view class="cu-item" :class="index == tabCur ? 'text-white cur' : ''" v-for="(item, index) in 3" v-key='index' :data-id='index' @click="tabSelect">Tab{{index}}</view>
			</scroll-view>
		</view>
		<view class="bg-white margin-top">
			<view class="cu-bar">
				<view class="action">
					<text class="cuIcon-title text-orange"></text> 图标
				</view>
			</view>
			<scroll-view scroll-x class='nav text-center bg-green' scroll-with-animation scroll-left="scrollLeft">
				<view class="cu-item" :class="tabCur == 0 ? 'text-white cur' : ''" data-id='0' @click="tabSelect">
					<text class="cuIcon-camerafill"></text> 数码
				</view>
				<view class="cu-item" :class="tabCur == 1 ? 'text-white cur' : ''" data-id='1' @click="tabSelect">
					<text class="cuIcon-upstagefill"></text> 排行榜
				</view>
				<view class="cu-item" :class="tabCur == 2 ? 'text-white cur' : ''" data-id='2' @click="tabSelect">
					<text class="cuIcon-clothesfill"></text> 皮肤
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabCur: 0,
				scrollLeft: 0
			}
		},
		methods: {
			tabSelect(e) {
				let that = this
				that.tabCur = e.currentTarget.dataset.id
				that.scrollLeft = (e.currentTarget.dataset.id-1)*60
			}
		}
	}
</script>

<style>

</style>
