<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-blue' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>按钮/设计</view>
		</cu-custom>
		<view class="padding-lg">
			<view class="box bg-white text-center radius">
				<button class="cu-btn " :class="(border ? 'line':'bg') + (bordersize ? bordersize : '') + '-' + color + ' ' + (round ? 'round' : '') + ' ' + (size) + ' ' + (shadow ? 'shadow' : '')">我是一个按钮</button>
			</view>
			<view class="padding text-center"><text style="margin-right: 10rpx;">class="cu-btn</text><text v-if="color">{{border?'line':'bg'}}{{bordersize?bordersize:''}}-{{color}}{{round?'round':''}} {{size}} {{shadow?'shadow':''}}</text>" </view>
		</view>
		<view class="cu-form-group margin-top" @click="showModal" data-target="ColorModal">
			<view class="title">选择颜色</view>
			<view class="padding solid radius shadow-blur" :class="'bg-' + color"></view>
		</view>
		<view class="cu-form-group">
			<view class="title">是否圆角</view>
			<switch class="sm" @change="setRound" />
		</view>
		<view class="cu-form-group">
			<view class="title">选择尺寸</view>
			<radio-group @change="setSize">
				<label class="margin-left-sm">
					<radio class="blue sm radio" value="sm"></radio>
					<text> 小</text>
				</label>
				<label class="margin-left-sm">
					<radio class="blue sm radio" value="" checked></radio>
					<text> 中</text>
				</label>
				<label class="margin-left-sm">
					<radio class="blue sm radio" value="lg"></radio>
					<text> 大</text>
				</label>
			</radio-group>
		</view>
		<view class="cu-form-group">
			<view class="title">是否添加阴影</view>
			<switch class="sm" @change="setShadow" />
		</view>
		<view class="cu-form-group">
			<view class="title">是否镂空</view>
			<switch class="sm" @change="setBorder" />
		</view>
		<view class="cu-form-group" v-if="border">
			<view class="title">边框大小</view>
			<radio-group @change="setBorderSize">
				<label class="margin-left-sm">
					<radio class="blue sm radio" value="" checked></radio>
					<tex>小</tex>
				</label>
				<label class="margin-left-sm">
					<radio class="blue sm radio" value="s"></radio>
					<tex>大</tex>
				</label>
			</radio-group>
		</view>
		<view class="cu-modal" :class="modalName == 'ColorModal' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="cu-bar justify-end solid-bottom">
					<view class="content">选择颜色</view>
					<view class="action" @click="hideModal">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="grid col-5 padding">
					<view class="padding-xs" v-for="(item, index) in ColorList" v-key @click="setColor" :data-color="item.name">
						<view class="padding-tb radius" :class="'bg-' + item.name"> {{item.title}} </view>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				border: '',
				round: '',
				size: '',
				shadow: '',
				bordersize: '',
				color: 'red',
				modalName: '',
				ColorList: [{
						title: '嫣红',
						name: 'red',
						color: '#e54d42'
					},
					{
						title: '桔橙',
						name: 'orange',
						color: '#f37b1d'
					},
					{
						title: '明黄',
						name: 'yellow',
						color: '#fbbd08'
					},
					{
						title: '橄榄',
						name: 'olive',
						color: '#8dc63f'
					},
					{
						title: '森绿',
						name: 'green',
						color: '#39b54a'
					},
					{
						title: '天青',
						name: 'cyan',
						color: '#1cbbb4'
					},
					{
						title: '海蓝',
						name: 'blue',
						color: '#0081ff'
					},
					{
						title: '姹紫',
						name: 'purple',
						color: '#6739b6'
					},
					{
						title: '木槿',
						name: 'mauve',
						color: '#9c26b0'
					},
					{
						title: '桃粉',
						name: 'pink',
						color: '#e03997'
					},
					{
						title: '棕褐',
						name: 'brown',
						color: '#a5673f'
					},
					{
						title: '玄灰',
						name: 'grey',
						color: '#8799a3'
					},
					{
						title: '草灰',
						name: 'gray',
						color: '#aaaaaa'
					},
					{
						title: '墨黑',
						name: 'black',
						color: '#333333'
					},
					{
						title: '雅白',
						name: 'white',
						color: '#ffffff'
					},
				]
			}
		},
		methods: {
			setRound(e) {
				let that = this
				that.round = e.detail.value
			},
			setSize(e) {
				let that = this
				that.size = e.detail.value
			},
			setShadow(e) {
				let that = this
				that.shadow = e.detail.value
			},
			setBorder(e) {
				let that = this
				that.border = e.detail.value
				if (!e.detail.value) {
					that.bordersize = false
				}
			},
			setBorderSize(e) {
				let that = this
				that.bordersize = e.detail.value
			},
			showModal(e) {
				let that = this
				that.modalName = e.currentTarget.dataset.target
			},
			hideModal() {
				let that = this
				that.modalName = ''
			},
			setColor(e) {
				let that = this
				that.color = e.currentTarget.dataset.color
				that.modalName = ''
			}
		}
	}
</script>

<style>
	.box {
		display: flex;
		align-items: center;
		justify-content: center;
		height: 200rpx;
	}
</style>
