<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-blue' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>按钮</view>
		</cu-custom>
		<view class="cu-bar bg-white solid-bottom">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>按钮形状
			</view>
			<navigator class="action" url="design" hover-class="none">
				<text class="cuIcon-skinfill"></text>
				<text class="text-df">设计</text>
			</navigator>
		</view>
		<view class="padding flex flex-wrap justify-between align-center bg-white">
			<button class="cu-btn">默认</button>
			<button class="cu-btn round">圆角</button>
			<button class="cu-btn icon">
				<text class="cuIcon-emojifill"></text>
			</button>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>按钮尺寸
			</view>
		</view>
		<view class="padding flex flex-wrap justify-between align-center bg-white">
			<button class="cu-btn round sm">小尺寸</button>
			<button class="cu-btn round">默认</button>
			<button class="cu-btn round lg">大尺寸</button>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>按钮颜色
			</view>
			<view class="action">
				<text class="text-df margin-right-sm">阴影</text>
				<switch class="sm" @change='setShadow'></switch>
			</view>
		</view>
		<view class="grid col-5 padding-sm">
			<view class="margin-tb-sm text-center" v-for="(item, index) in ColorList" v-key='index'>
				<button class="cu-btn round" :class="'bg-' + item.name + ' ' + (shadow ? 'shadow': '')">{{item.title}}</button>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-blue"></text>镂空按钮
			</view>
			<view class="action">
				<radio-group @change="setBorderSize">
					<label class="margin-left-sm">
						<radio class="blue sm radio" value="" checked></radio>
						<text> 小</text>
					</label>
					<label class="margin-left-sm">
						<radio class="blue sm radio" value="s"></radio>
						<text> 大</text>
					</label>
				</radio-group>
			</view>
		</view>
		<view class="grid col-5 padding-sm">
			<view class="margin-tb-sm text-center" v-for="(item, index) in ColorList" v-key='index'>
				<button class="cu-btn round" :class="'line' + (bordersize ? bordersize : '') + '-' + item.name + ' ' + (shadow ? 'shadow': '')">{{item.title}}</button>
			</view>
		</view>
		<view class="cu-bar margin-top bg-white">
		  <view class="action">
		    <text class="cuIcon-title text-blue"></text>块状按钮
		  </view>
		</view>
		<view class="padding flex flex-direction">
			<button class="cu-btn bg-grey lg">玄灰</button>
			<button class="cu-btn bg-red lg margin-tb-sm">嫣红</button>
		</view>
		<view class="cu-bar margin-top bg-white">
		  <view class="action">
		    <text class="cuIcon-title text-blue"></text>无效状态
		  </view>
		</view>
		<view class="padding flex flex-direction">
			<button class="cu-btn block bg-blue lg" disabled type="">无效状态</button>
			<button class="cu-btn block line-blue lg margin-tb-sm" disabled>无效状态</button>
		</view>
		<view class="cu-bar margin-top bg-white">
		  <view class="action">
		    <text class="cuIcon-title text-blue"></text>按钮加图标
		  </view>
		</view>
		<view class="padding">
			<button class="cu-btn block line-orange lg">
				<text class="cuIcon-upload"></text>图标
			</button>
			<button class="cu-btn block bg-blue margin-tb-sm lg">
				<text class="cuIcon-loading2 cuIconfont-spin"></text>加载
			</button>
			<button class="cu-btn block bg-black margin-tb-sm lg" loading>
				微信加载
			</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				shadow: false,
				bordersize: '',
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
			setShadow(e) {
				this.shadow = e.detail.value
			},
			setBorderSize(e) {
				this.bordersize = e.detail.value
			}
		}
	}
</script>

<style>

</style>
