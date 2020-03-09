<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isCustom='ture'>
			<view slot='content'>操作条</view>
		</cu-custom>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-green"></text>底部操作条
			</view>
		</view>
		<view class="box">
			<view class="cu-bar tabbar bg-white">
				<view class="action">
					<view class="cuIcon-cu-image">
						<image src="../../../static/tabbar/basics_cur.png" mode=""></image>
					</view>
					<view class="text-green">元素</view>
				</view>
				<view class="action">
					<view class="cuIcon-cu-image">
						<image src="../../../static/tabbar/component.png" mode=""></image>
					</view>
					<view class="text-gray">组件</view>
				</view>
				<view class="action">
					<view class="cuIcon-cu-image">
						<image src="../../../static/tabbar/plugin.png" mode=""></image>
						<view class="cu-tag badge">99</view>
					</view>
					<view class="text-gray">扩展</view>
				</view>
				<view class="action">
					<view class="cuIcon-cu-image">
						<image src="../../../static/tabbar/about.png" mode=""></image>
						<view class="cu-tag badge"></view>
					</view>
					<view class="text-gray">关于</view>
				</view>
			</view>
			<view class="cu-bar tabbar bg-black margin-bottom-xl">
				<view class="action text-orange">
					<view class="cuIcon-homefill"></view> 首页
				</view>
				<view class="action text-gray">
					<view class="cuIcon-similar"></view> 分类
				</view>
				<view class="action text-gray">
					<view class="cuIcon-recharge"></view> 积分
				</view>
				<view class="action text-gray">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view> 购物车
				</view>
				<view class="action text-gray">
					<view class="cuIcon-my">
						<view class="cu-tag badge"></view>
					</view> 我的
				</view>
			</view>
			<view class="cu-bar tabbar bg-white margin-bottom-xl">
				<view class="action text-green">
					<view class="cuIcon-homefill"></view> 首页
				</view>
				<view class="action text-gray">
					<view class="cuIcon-similar"></view> 分类
				</view>
				<view class="action text-gray add-action">
					<button class="cu-btn cuIcon-add bg-green shadow"></button> 发布
				</view>
				<view class="action text-gray">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view> 购物车
				</view>
				<view class="action text-gray">
					<view class="cuIcon-my">
						<view class="cu-tag badge"></view>
					</view> 我的
				</view>
			</view>
			<view class="cu-bar tabbar bg-black">
				<view class="action text-green">
					<view class="cuIcon-homefill"></view> 首页
				</view>
				<view class="action text-gray">
					<view class="cuIcon-similar"></view> 分类
				</view>
				<view class="action text-gray add-action">
					<button class="cu-btn cuIcon-add bg-green shadow"></button> 发布
				</view>
				<view class="action text-gray">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view> 购物车
				</view>
				<view class="action text-gray">
					<view class="cuIcon-my">
						<view class="cu-tag badge"></view>
					</view> 我的
				</view>
			</view>
			<view class="cu-bar tabbar bg-white border shop">
				<button class="action" open-type="contact">
					<view class="cuIcon-service text-green">
						<view class="cu-tag badge"></view>
					</view>
					客服
				</button>
				<view class="action text-orange">
					<view class="cuIcon-favorfill"></view> 已收藏
				</view>
				<view class="action text-gray">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view>
					购物车
				</view>
				<view class="bg-red submit">立即订购</view>
			</view>
			<view class="cu-bar tabbar bg-white border shop">
				<button class="action" open-type="contact">
					<view class="cuIcon-service text-green">
						<view class="cu-tag badge"></view>
					</view>
					客服
				</button>
				<view class="action text-gray">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view>
					购物车
				</view>
				<view class="bg-orange submit">加入购物车</view>
				<view class="bg-red submit">立即订购</view>
			</view>
			<view class="cu-bar tabbar bg-white border shop">
				<button class="action" open-type="contact">
					<view class="cuIcon-service text-green">
						<view class="cu-tag badge"></view>
					</view>
					客服
				</button>
				<view class="action">
					<view class="cuIcon-shop text-gray"></view> 店铺
				</view>
				<view class="action">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view>
					购物车
				</view>
				<view class="btn-group">
					<button class="cu-btn bg-red round shadow-blur">立即订购</button>
				</view>
			</view>
			<view class="cu-bar tabbar bg-white border shop">
				<button class="action" open-type="contact">
					<view class="cuIcon-service text-green">
						<view class="cu-tag badge"></view>
					</view>
					客服
				</button>
				<view class="action">
					<view class="cuIcon-cart">
						<view class="cu-tag badge">99</view>
					</view>
					购物车
				</view>
				<view class="btn-group">
					<button class="cu-btn bg-orange round shadow-blur">加入购物车</button>
					<button class="cu-btn bg-red round shadow-blur">立即订购</button>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white">
			<view class="action">
				<text class="cuIcon-title text-green"></text>标题操作条
			</view>
		</view>
		<view class="box">
			<view class="cu-bar bg-white">
				<view class="action border-title">
					<text class="text-xl text-bold">关于我们</text>
					<text class="bg-grey" style="width: 2rem;"></text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action border-title">
					<text class="text-xl text-bold text-blue">关于我们</text>
					<text class="bg-gradual-blue" style="width: 3rem;"></text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action sub-title">
					<text class="text-xl text-bold text-green">关于我们</text>
					<text class="bg-green"></text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action sub-title">
					<text class="text-xl text-bold text-blue">关于我们</text>
					<text class="text-ABC text-blue">about</text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action title-style-3">
					<text class="text-xl text-bold">关于我们</text>
					<text class="text-Abc text-gray self-end margin-left-sm">about</text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action">
					<text class="cuIcon-title text-green"></text>
					<text class="text-xl text-bold">关于我们</text>
				</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action">
					<text class="cuIcon-titles text-green"></text>
					<text class="text-xl text-bold">关于我们</text>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-green"></text>顶部操作条
			</view>
		</view>
		<view class="box">
			<view class="cu-bar bg-white">
				<view class="action">
					<text class="cuIcon-back text-gray"></text> 返回
				</view>
				<view class="content text-bold">操作条</view>
			</view>
			<view class="cu-bar bg-white">
				<view class="action">
					<text class="cuIcon-homefill text-gray"></text> 首页
				</view>
				<view class="content text-bold">鲜亮的高饱和色彩，专注视觉的小程序组件库</view>
				<view class="action">
					<text class="cuIcon-cardboardfill text-grey"></text>
					<text class="cuIcon-recordfill text-red"></text>
				</view>
			</view>
			<view class="cu-bar bg-blue">
				<view class="action">
					<text class="cuIcon-close"></text> 关闭
				</view>
				<view class="content text-bold">海蓝</view>
			</view>
			<view class="cu-bar bg-black">
				<view class="cu-avatar round" style="background-image:url(https://image.weilanwl.com/img/square-3.jpg);"></view>
				<view class="content">ColorUI</view>
				<view class="action">
					<text class="cuIcon-more"></text>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-green"></text>搜索操作条
			</view>
		</view>
		<view class="box">
			<view class="cu-bar bg-white search">
				<view class="search-form round">
					<text class="cuIcon-search"></text>
					<input type="text" placeholder="搜索图片、文章、视频" confirm-type="search">
				</view>
				<view class="action">
					<button class="cu-btn round bg-green shadow-blur">搜索</button>
				</view>
			</view>
			<view class="cu-bar bg-white search">
				<view class="cu-avatar round" style="background-image:url(https://image.weilanwl.com/img/square-1.jpg);"></view>
				<view class="search-form round">
					<text class="cuIcon-search"></text>
					<input type="text" placeholder="搜索图片、文章、视频" confirm-type="search">
				</view>
				<view class="action">
					<text>北京</text>
					<text class="cuIcon-triangledownfill"></text>
				</view>
			</view>
			<view class="cu-bar bg-red search">
				<view class="cu-avatar round" style="background-image:url(https://image.weilanwl.com/img/square-1.jpg);"></view>
				<view class="search-form radius">
					<text class="cuIcon-search"></text>
					<input type="text" placeholder="搜索图片、文章、视频" confirm-type="search">
				</view>
				<view class="action">
					<text>北京</text>
					<text class="cuIcon-triangledownfill"></text>
				</view>
			</view>
			<view class="cu-bar bg-cyan search">
				<view class="search-form radius">
					<text class="cuIcon-search"></text>
					<input type="text" placeholder="搜索图片、文章、视频" confirm-type="search">
				</view>
				<view class="action">
					<text class="cuIcon-close"></text>
					<text>取消</text>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-green"></text>操作条按钮组
			</view>
		</view>
		<view class="box">
			<view class="cu-bar btn-group">
				<button class="cu-btn bg-green shadow-blur round lg">保存</button>
			</view>
			<view class="cu-bar btn-group">
				<button class="cu-btn bg-green shadow-blur radius">保存</button>
				<button class="cu-btn line-green shadow-blur radius">上传</button>
			</view>
			<view class="cu-bar btn-group">
				<button class="cu-btn bg-green shadow-blur round">保存</button>
				<button class="cu-btn bg-blue shadow-blur round">提交</button>
			</view>
		</view>
		<view class="cu-bar bg-white solid-bottom margin-top">
			<view class="action">
				<text class="cuIcon-title text-green"></text>输入操作条
			</view>
		</view>
		<view class="box">
			<view class="cu-bar input">
				<view class="action">
					<text class="cuIcon-sound text-grey"></text>
				</view>
				<input type="text" class="solid-bottom" focus="false" cursor-spacing="10" maxlength="300">
				<view class="action">
					<text class="cuIcon-emojifill text-grey"></text>
				</view>
				<button class="cu-btn bg-green shadow-blur">发送</button>
			</view>
			<view class="cu-bar input">
				<view class="cu-avatar round" style="background-image: url('https://image.weilanwl.com/img/square-3.jpg');"></view>
				<view class="action">
					<text class="cuIcon-roundaddfill text-grey"></text>
				</view>
				<input type="text" class="solid-bottom" focus="false" cursor-spacing="10" maxlength="300">
				<view class="action">
					<text class="cuIcon-emojifill text-grey"></text>
				</view>
				<button class="cu-btn bg-green shadow-blur">发送</button>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			
		}
	}
</script>

<style>
.box{
	margin: 20rpx 0;
}
.box view.cu-bar{
	margin-top: 20rpx;
}
</style>
