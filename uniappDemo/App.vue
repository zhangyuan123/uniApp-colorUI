<script>
	import Vue from 'vue'
	export default {
		data() {
			return {
				
			}
		},
		onLaunch: function() {
			console.log('App Launch')
			uni.getSystemInfo({
				success: function(e) {
					// #ifndef MP
					Vue.prototype.StatusBar = e.statusBarHeight;
					if (e.platform == 'android') {
						Vue.prototype.CustomBar = e.statusBarHeight + 50;
					} else {
						Vue.prototype.CustomBar = e.statusBarHeight + 45;
					};
					// #endif

					// #ifdef MP
					Vue.prototype.StatusBar = e.statusBarHeight;
					let custom = wx.getMenuButtonBoundingClientRect();
					Vue.prototype.Custom = custom;
					Vue.prototype.CustomBar = custom.bottom + custom.top - e.statusBarHeight;
					// #endif
				}
			})
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	@import url("colorui/main.css");
	@import url("colorui/icon.css");

	.content {
		width: 100%;
	}

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
