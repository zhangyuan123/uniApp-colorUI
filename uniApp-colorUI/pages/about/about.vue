<template>
	<view class="content">
		<view class="UCenter-bg">
			<image src="../../static/coloruiLogo.png" class="png" mode="widthFix"></image>
			<view class="text-xl">ColorUI组件库
				<text class="text-df">v2.0</text>
			</view>
			<view class="margin-top-sm">
				<text>Cover By:文晓港</text>
			</view>
			<image src="https://raw.githubusercontent.com/weilanwl/ColorUI/master/demo/images/wave.gif" mode="scaleToFill" class="gif-wave"></image>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		}
	}
</script>

<style>
	.UCenter-bg {
	  background-image: url(https://image.weilanwl.com/color2.0/index.jpg);
	  background-size: cover;
	  height: 550rpx;
	  display: flex;
	  justify-content: center;
	  padding-top: 40rpx;
	  overflow: hidden;
	  position: relative;
	  flex-direction: column;
	  align-items: center;
	  color: #fff;
	  font-weight: 300;
	  text-shadow: 0 0 3px rgba(0, 0, 0, 0.3);
	}
	
	.UCenter-bg text {
	  opacity: 0.8;
	}
	
	.UCenter-bg image {
	  width: 200rpx;
	  height: 200rpx;
	}
	
	.UCenter-bg .gif-wave{
	  position: absolute;
	  width: 100%;
	  bottom: 0;
	  left: 0;
	  z-index: 99;
	  mix-blend-mode: screen;  
	  height: 100rpx;   
	}
	
	map,.mapBox{
	  left: 0;
	  z-index: 99;
	  mix-blend-mode: screen;  
	  height: 100rpx;   
	}
	
	map,.mapBox{
	  width: 750rpx;
	  height: 300rpx;
	}
</style>
