<template>
	<view class="content" style="background-color: #1CBBB4;height: 100vh;">
		<scroll-view scroll-y class="DrawerPage" :class="modalName == 'viewModal' ? 'show' : ''">
			<cu-custom bgColor='bg-gradual-blue' isBack='ture'>
				<view slot='backText'>返回</view>
				<view slot='content'>全屏抽屉</view>
			</cu-custom>
			<view class="padding margin text-center">
				<view class="cu-btn bg-green lg block shadow radius margin-xl" data-target='viewModal' @click="showModal">
					打开抽屉
				</view>
			</view>
			<view class="cu-list menu card-menu margin-top-xl margin-bottom-xl shadow-lg">
				<view class="cu-item arrow" v-for="(item, index) in 20" v-key>
					<view class="content">
						<text class="cuIcon-github text-grey"></text>
						<text class="text-grey">{{index + 1}}</text>
					</view>
				</view>
			</view>
			<view class="padding margin text-center">
				<view class="cu-btn bg-green lg block shadow radius margin-xl" data-target='viewModal' @click="showModal">
					打开抽屉
				</view>
			</view>
		</scroll-view>
		<view class="DrawerClose" :class="modalName == 'viewModal' ? 'show' : ''" @click="hideModal">
			<text class="cuIcon-pullright"></text>
		</view>
		<scroll-view scroll-y class="DrawerWindow" :class="modalName == 'viewModal' ? 'show' : ''">
			<view class="cu-list menu card-menu margin-top-xl margin-bottom-xl shadow-lg">
				<view class="cu-item arrow" v-for="(item, index) in 20" v-key>
					<view class="content">
						<text class="cuIcon-github text-grey"></text>
						<text class="text-grey">{{index + 1}}</text>
					</view>
				</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				modalName: ''
			}
		},
		methods: {
			showModal(e) {
				let that = this
				that.modalName = e.currentTarget.dataset.target
			},
			hideModal() {
				let that = this
				that.modalName = null
			}
		}
	}
</script>

<style>
	.DrawerPage {
		position: fixed;
		width: 100vw;
		height: 100vh;
		left: 0vw;
		background-color: #f1f1f1;
		transition: all 0.4s;
	}

	.DrawerPage.show {
		transform: scale(0.9, 0.9);
		left: 85vw;
		box-shadow: 0 0 60rpx rgba(0, 0, 0, 0.2);
		transform-origin: 0;
	}

	.DrawerWindow {
		position: absolute;
		width: 85vw;
		height: 100vh;
		left: 0;
		top: 0;
		transform: scale(0.9, 0.9) translateX(-100%);
		opacity: 0;
		pointer-events: none;
		transition: all 0.4s;
	}

	.DrawerWindow.show {
		transform: scale(1, 1) translateX(0%);
		opacity: 1;
		pointer-events: all;
	}

	.DrawerClose {
		position: absolute;
		width: 40vw;
		height: 100vh;
		right: 0;
		top: 0;
		color: transparent;
		padding-bottom: 30rpx;
		display: flex;
		align-items: flex-end;
		justify-content: center;
		background-image: linear-gradient(90deg, rgba(0, 0, 0, 0.01), rgba(0, 0, 0, 0.6));
		letter-spacing: 5px;
		font-size: 50rpx;
		opacity: 0;
		pointer-events: none;
		transition: all 0.4s;
	}

	.DrawerClose.show {
		opacity: 1;
		pointer-events: all;
		width: 15vw;
		color: #fff;
	}

	.DrawerPage .cu-bar.tabbar .action button.icon {
		width: 64rpx;
		height: 64rpx;
		line-height: 64rpx;
		margin: 0;
		display: inline-block;
	}

	.DrawerPage .cu-bar.tabbar .action .cu-avatar {
		margin: 0;
	}

	.DrawerPage .nav {
		flex: 1;
	}

	.DrawerPage .nav .cu-item.cur {
		border-bottom: 0;
		position: relative;
	}

	.DrawerPage .nav .cu-item.cur::after {
		content: "";
		width: 10rpx;
		height: 10rpx;
		background-color: currentColor;
		position: absolute;
		bottom: 10rpx;
		border-radius: 10rpx;
		left: 0;
		right: 0;
		margin: auto;
	}

	.DrawerPage .cu-bar.tabbar .action {
		flex: initial;
	}
</style>
