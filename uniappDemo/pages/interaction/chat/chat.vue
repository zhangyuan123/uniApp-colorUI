<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>聊天</view>
		</cu-custom>
		<view class="cu-chat">
			<view class="cu-item self">
				<view class="main">
					<view class="content bg-green shadow">
						<text>喵喵喵！喵喵喵！喵喵喵！喵喵！喵喵！！喵！喵喵喵！</text>
					</view>
				</view>
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big107000.jpg');"></view>
				<view class="date">2018年3月23日 13:23</view>
			</view>
			<view class="cu-info round">对方撤回一条消息!</view>
			<view class="cu-item">
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big143004.jpg');"></view>
				<view class="main">
					<view class="content shadow">
						<text>喵喵喵！喵喵喵！</text>
					</view>
				</view>
				<view class="date">13:23</view>
			</view>
			<view class="cu-info round">
				<text class="cuIcon-roundclosefill text-red"></text> 对方拒绝了你的消息
			</view>
			<view class="cu-info">
				对方开启了好友验证，你还不是他(她)的好友。请先发送好友验证请求，对方验证通过后，才能聊天。
				<text class="text-blue">发送好友验证</text>
			</view>
			<view class="cu-item self">
				<view class="main">
					<image src="https://ossweb-img.qq.com/images/lol/web201310/skin/big10006.jpg" class="radius" mode="widthFix"></image>
				</view>
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big107000.jpg');"></view>
				<view class="date">15:47</view>
			</view>
			<view class="cu-item self">
				<view class="main">
					<view class="action text-bold text-grey">3"</view>
					<view class="content bg-green shadow">
						<text class="cuIcon-sound text-xxl padding-right-xl"></text>
					</view>
				</view>
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big107000.jpg');"></view>
				<view class="date">16:03</view>
			</view>
			<view class="cu-item self">
				<view class="main">
					<view class="action">
						<text class="cuIcon-locationfill text-orange text-xxl"></text>
					</view>
					<view class="content bg-green shadow">喵星球，喵喵市</view>
				</view>
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big107000.jpg');"></view>
				<view class="date">16:05</view>
			</view>
			<view class="cu-item">
				<view class="cu-avatar radius" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big143004.jpg');"></view>
				<view class="main">
					<view class="content shadow">
						<text>@#$^&**</text>
					</view>
					<view class="action">
						<text class="cuIcon-warnfill text-red text-xxl"></text>
					</view>
				</view>
				<view class="date">16:20</view>
			</view>
		</view>
		<view class="cu-bar foot input" :class="inputBottom != 0 ? 'cur' : ''" :style="{bottom: inputBottom + 'px'}">
			<view class="action">
				<text class="cuIcon-sound text-grey"></text>
			</view>
			<input type="text" class="solid-bottom" adjust-position="false" focus="false" maxlength="300" cursor-spacing="10" @focus="inputFocus" @blur="inputBlur">
			<view class="action">
				<text class="cuIcon-emojifill text-grey"></text>
			</view>
			<button class="cu-btn bg-green shadow">发送</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				inputBottom: 0
			}
		},
		methods: {
			inputFocus(e) {
				let that = this
				that.inputBottom = e.detail.height
			},
			inputBlur() {
				let that = this
				that.inputBottom = 0
			}
		}
	}
</script>

<style>
page{
	padding-bottom: 100rpx;
}
</style>
