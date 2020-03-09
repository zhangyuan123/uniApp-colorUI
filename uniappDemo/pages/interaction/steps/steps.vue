<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>步骤条</view>
		</cu-custom>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 基本用法
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="basicsSteps">下一步</button>
			</view>
		</view>
		<view class="padding bg-white">
			<view class="cu-steps">
				<view class="cu-item" :class="index > basics ? '' : 'text-red'" v-for="(item, index) in basicsList" v-key>
					<text :class="'cuIcon-' + item.icon"></text> {{item.name}}
				</view>
			</view>
		</view>
		<view class="padding bg-white margin-top-xs">
			<view class="cu-steps">
				<view class="cu-item" :class="index > basics ? '' : 'text-orange'" v-for="(item, index) in basicsList" v-key>
					<text :class="'cuIcon-' + item.icon"></text> {{item.name}}
				</view>
			</view>
		</view>
		<view class="padding bg-white margin-top-xs">
			<view class="cu-steps">
				<view class="cu-item" :class="index > basics ? '' : 'text-blue'" v-for="(item, index) in basicsList" v-key>
					<text :class="'cuIcon-' + item.icon"></text> {{item.name}}
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 数字完成
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="numSteps">下一步</button>
			</view>
		</view>
		<view class="padding bg-white">
			<view class="cu-steps">
				<view class="cu-item" :class="index > num ? '' : 'text-blue'" v-for="(item, index) in numList" v-key>
					<text class="num" :class="index == 2 ? 'err' : ''" :data-index='index + 1'></text> {{item.name}}
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 多级显示
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="scrollSteps">下一步</button>
			</view>
		</view>
		<scroll-view scroll-x class="padding bg-white response cu-steps steps-bottom" :scroll-into-view="'scroll-' + scroll" scroll-with-animation>
			<view class="cu-item padding-lr-xl" :class="index > scroll ? '' : 'text-blue'" v-for="(item, index) in 10" v-key :id="'scroll-' + index">
				Level {{index + 1}} <text class="num" :data-index="index + 1"></text>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				basicsList: [{
					icon: 'usefullfill',
					name: '开始'
				}, {
					icon: 'radioboxfill',
					name: '等待'
				}, {
					icon: 'roundclosefill',
					name: '错误'
				}, {
					icon: 'roundcheckfill',
					name: '完成'
				}, ],
				basics: 0,
				numList: [{
					name: '开始'
				}, {
					name: '等待'
				}, {
					name: '错误'
				}, {
					name: '完成'
				}, ],
				num: 0,
				scroll: 0
			}
		},
		methods: {
			basicsSteps() {
				let that = this
				that.basics = that.basics == that.basicsList.length - 1 ? 0 : that.basics + 1
			},
			numSteps() {
				let that = this
				that.num = that.num == that.numList.length - 1 ? 0 : that.num + 1
			},
			scrollSteps() {
				let that = this
				that.scroll = that.scroll == 9 ? 0 : that.scroll + 1
			}
		}
	}
</script>

<style>

</style>
