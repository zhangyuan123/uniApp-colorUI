<template>
	<view class="content">
		<cu-custom bgImage='https://image.weilanwl.com/color2.0/plugin/sylb2244.jpg' isBack='true'>
			<view slot="backText">返回</view>
			<view slot='content'>索引</view>
		</cu-custom>
		<view class="cu-bar bg-white search fixed" :style="{top: CustomBar + 'px'}">
			<view class="search-form round">
				<text class="cuIcon-search"></text>
				<input type="text" placeholder="输入搜索的关键词" confirm-type="search">
			</view>
			<view class="action">
				<button class="cu-btn bg-gradual-green shadow-blur round">搜索</button>
			</view>
		</view>
		<scroll-view class="indexes" scroll-y :scroll-into-view="'indexes-' + listCurID" :style="scrollStyle"
		 scroll-with-animation="true" enable-back-to-top="true">
			<block v-for="(item, index) in list" v-key='index'>
				<view class="padding" :class="'indexItem-' + list[index]" :id="'indexes-' + list[index]" :data-index="list[index]">
					{{item}}
				</view>
				<view class="cu-list menu-avatar no-padding">
					<view class="cu-item" v-for="(childItem, childId) in 2" v-key='childId'>
						<view class="cu-avatar round lg">{{item}}</view>
						<view class="content">
							<view class="text-grey">{{item}}
								<text class="text-abc">{{childItem}}</text>君</view>
							<view class="text-gray text-sm">
								有{{childId+2}}个主子需要伺候
							</view>
						</view>
					</view>
				</view>
			</block>
		</scroll-view>
		<view class="indexBar" :style="barStyle">
			<view class="indexBar-box" @touchmove="tMove" @touchstart="tStart" @touchend="tEnd">
				<view class="indexBar-item" v-for="(item, index) in list" v-key :id='index' @touchstart='getCur' @touchend="setCur">{{item}}</view>
			</view>
		</view>
		<!--选择显示-->
		<view :hidden="hidden" class="indexToast">
			{{listCur}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				CustomBar: this.CustomBar,
				list: [],
				listCur: '',
				listCurID: '',
				boxTop: 0,
				barTop: 0,
				hidden: true
			}
		},
		computed: {
			scrollStyle() {
				let that = this
				let CustomBar = that.CustomBar
				// var style = `height:calc${(1350 - CustomBar)}px` calc(100vh-${CustomBar}px)
				var style = `position: absolute;top: ${(CustomBar + 50)}px;height: calc(100vh - ${CustomBar}px - 50px)`
				return style;
			},
			barStyle() {
				let that = this
				let CustomBar = that.CustomBar
				var style = `height: calc(100vh - ${CustomBar}px - 50px)`
				return style;
			}
		},
		created() {
			let that = this;
			uni.createSelectorQuery().select('.indexBar-box').boundingClientRect(function(res) {
				console.log(res)
				that.boxTop = res.top
			}).exec();
			uni.createSelectorQuery().select('.indexes').boundingClientRect(function(res) {
				that.barTop = res.top
			}).exec()
		},
		mounted() {
			let that = this
			that.initList()
		},
		methods: {
			initList() {
				let that = this
				let list = []
				for (let i = 0; i < 26; i++) {
					list[i] = String.fromCharCode(65 + i)
				}
				that.list = list
				that.listCur = list[0]
			},
			//获取文字信息
			getCur(e) {
				let that = this
				that.hidden = false
				that.listCur = that.list[e.target.id]
			},
			setCur(e) {
				let that = this
				that.hidden = true
			},
			tMove(e) {
				let y = e.touches[0].clientY,
					offsettop = this.data.boxTop,
					that = this;
				//判断选择区域,只有在选择区才会生效
				if (y > offsettop) {
					let num = parseInt((y - offsettop) / 20);
					that.listCur = that.list[num]
				};
			},
			tStart() {
				let that = this
				that.hidden = false
			},
			tEnd() {
				let that = this
				that.hidden = true
				that.listCurID = that.listCur
			}
		}
	}
</script>

<style>
	.indexes {
		position: relative;
	}

	.indexBar {
		position: fixed;
		right: 0px;
		bottom: 0px;
		padding: 20rpx 20rpx 20rpx 60rpx;
		display: flex;
		align-items: center;
	}

	.indexBar .indexBar-box {
		width: 40rpx;
		height: auto;
		background: #fff;
		display: flex;
		flex-direction: column;
		box-shadow: 0 0 20rpx rgba(0, 0, 0, 0.1);
		border-radius: 10rpx;
	}

	.indexBar-item {
		flex: 1;
		width: 40rpx;
		height: 40rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 24rpx;
		color: #888;
	}

	movable-view.indexBar-item {
		width: 40rpx;
		height: 40rpx;
		z-index: 9;
		position: relative;
	}

	movable-view.indexBar-item::before {
		content: "";
		display: block;
		position: absolute;
		left: 0;
		top: 10rpx;
		height: 20rpx;
		width: 4rpx;
		background-color: #f37b1d;
	}

	.indexToast {
		position: fixed;
		top: 0;
		right: 80rpx;
		bottom: 0;
		background: rgba(0, 0, 0, 0.5);
		width: 100rpx;
		height: 100rpx;
		border-radius: 10rpx;
		margin: auto;
		color: #fff;
		line-height: 100rpx;
		text-align: center;
		font-size: 48rpx;
	}
</style>
