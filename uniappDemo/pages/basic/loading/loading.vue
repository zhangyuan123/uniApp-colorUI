<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-blue' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>加载</view>
		</cu-custom>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>背景
			</view>
		</view>
		<view class="cu-load bg-blue" :class="!isLoad ? 'loading':'over'"></view>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>加载状态
			</view>
			<view class="action">
				<switch class="sm" @change="isLoading" />
			</view>
		</view>
		<view class="cu-load bg-grey" :class="!isLoad ? 'loading':'over'"></view>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>加载错误
			</view>
		</view>
		<view class="cu-load bg-red erro"></view>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>弹窗加载
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="loadModal">点我</button>
			</view>
		</view>
		<view class="cu-load load-modal" v-if="isLoadModal">
			<image src="../../../static/logo.png" class="png" mode="aspectFit"></image>
			<view class="text-gray">加载中...</view>
		</view>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>进度条加载
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="loadProgress">点我</button>
			</view>
		</view>
		<view class='load-progress' :class="loadProgressNum != 0 ? 'show':'hide'" :style="{top:CustomBar + 'px'}">
		  <view class='load-progress-bar bg-green'></view>
		  <view class='load-progress-spinner text-green'></view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isLoad: '',
				isLoadModal: false,
				CustomBar: this.CustomBar,
				loadProgressNum: 0
			}
		},
		methods: {
			isLoading(e) {
				let that = this
				that.isLoad = e.detail.value
			},
			loadModal() {
				let that = this
				that.isLoadModal = true
				console.log(that.isLoadModal)
				setTimeout(function() {
					that.isLoadModal = false
				}, 2000)
			},
			loadProgress() {
				let that = this
				console.log(that.loadProgressNum)
				that.loadProgressNum = that.loadProgressNum + 3
				if (that.loadProgressNum < 100) {
					setTimeout(function() {
						that.loadProgress()
					}, 100)
				}else {
					that.loadProgressNum = 0
				}
			}
		}
	}
</script>

<style>
</style>
