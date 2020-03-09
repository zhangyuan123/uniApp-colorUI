<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>模态框</view>
		</cu-custom>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 普通窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='Modal'>Modal</button>
			</view>
		</view>
		<view class="cu-modal" :class="modalName == 'Modal' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white justify-end">
					<view class="content">Modal标题</view>
					<view class="action" @click="hideModal">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="padding-xl">
					Modal内容
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 底部窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='bottomModal'>Bottom</button>
			</view>
		</view>
		<view class="cu-modal bottom-modal" :class="modalName == 'bottomModal' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white">
					<view class="action text-green" @click="hideModal">确定</view>
					<view class="action text-blue" @click="hideModal">取消</view>
				</view>
				<view class="padding-xl">
					Modal内容
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 对话窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='dialogModal1'>Dialog</button>
				<button class="cu-btn bg-blue shadow margin-left" @click="showModal" data-target='dialogModal2'>Dialog</button>
			</view>
		</view>
		<view class="cu-modal" :class="modalName == 'dialogModal1' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white justify-end">
					<view class="content">Modal标题</view>
					<view class="action" @click="hideModal">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="padding-xl">
					Modal 内容
				</view>
				<view class="cu-bar bg-white justify-end">
					<view class="action">
						<button class="cu-btn line-green text-green" @click="hideModal">取消</button>
						<button class="cu-btn bg-green margin-left" @click="hideModal">确定</button>
					</view>
				</view>
			</view>
		</view>
		<view class="cu-modal" :class="modalName == 'dialogModal2' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="cu-bar bg-white justify-end">
					<view class="content">Modal标题</view>
					<view class="action" @click="hideModal">
						<text class="cuIcon-close text-red"></text>
					</view>
				</view>
				<view class="padding-xl">
					Modal 内容
				</view>
				<view class="cu-bar bg-white">
					<view class="action margin-0 flex-sub text-green" @click="hideModal">
						<text class="cuIcon-moneybag"></text> 微信支付
					</view>
					<view class="action margin-0 flex-sub text-green solid-left" @click="hideModal">取消</view>
					<view class="action margin-0 flex-sub solid-left" @click="hideModal">确定</view>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 图片窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='imageModal'>Image</button>
			</view>
		</view>
		<view class="cu-modal" :class="modalName == 'imageModal' ? 'show' : ''">
			<view class="cu-dialog">
				<view class="bg-img" style="background-image: url('https://ossweb-img.qq.com/images/lol/web201310/skin/big91012.jpg');height: 200px;">
					<view class="cu-bar justify-end text-white">
						<view class="action" @click="hideModal">
							<text class="cuIcon-close"></text>
						</view>
					</view>
				</view>
				<view class="cu-bar bg-white">
					<view class="action margin-0 flex-sub solid-left" @click="hideModal">我知道了</view>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 单选窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='radioModal'>Radio</button>
			</view>
		</view>
		<view class="cu-modal" :class="modalName == 'radioModal' ? 'show' : ''" @click="hideModal">
			<view class="cu-dialog" @click.stop>
				<radio-group class="block">
					<view class="cu-list menu text-left">
						<view class="cu-item" v-for="(item, index) in 5" v-key='index'>
							<label class="flex justify-between flex-sub align-center">
								<view class="flex-sub">Item {{index + 1}}</view>
								<radio class="round"></radio>
							</label>
						</view>
					</view>
				</radio-group>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 多选窗口
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='chooseModal'>Choose</button>
			</view>
		</view>
		<view class="cu-modal bottom-modal" :class="modalName == 'chooseModal' ? 'show' : ''" @click="hideModal">
			<view class="cu-dialog" @click.stop>
				<view class="cu-bar bg-white">
					<view class="action text-blue" @click="hideModal">取消</view>
					<view class="action text-green" @click="hideModal">确定</view>
				</view>
				<view class="grid col-3 padding-sm">
					<view class="padding-xs" v-for="(item, index) in checkbox" v-key>
						<button class="cu-btn orange lg block" :class="item.checked ? 'bg-orange' : 'line-orange'" @click="chooseCheckbox" :data-value='item.value'>
							{{item.name}}
							<view class="cu-tag sm round" :class="item.checked ? 'bg-white text-orange' : 'bg-orange'" v-if="item.hot">HOT</view>
						</button>
					</view>
				</view>
			</view>
		</view>
		<view class="cu-bar bg-white margin-top">
			<view class="action">
				<text class="cuIcon-title text-orange"></text> 侧边抽屉
			</view>
			<view class="action">
				<button class="cu-btn bg-green shadow" @click="showModal" data-target='drawerModalL'>Left</button>
				<button class="cu-btn bg-green shadow margin-left" @click="showModal" data-target='drawerModalR'>Right</button>
			</view>
		</view>
		<view class="cu-modal drawer-modal justify-start" :class="modalName == 'drawerModalL' ? 'show' : 'hide'" @click="hideModal">
			<view class="cu-dialog basis-lg" @click.stop :style='drawerStyle'>
				<view class="cu-list menu text-left">
					<view class="cu-item arrow" v-for="(item, index) in 5" v-key>
						<view class="content">
							<view>Item {{index + 1}}</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="cu-modal drawer-modal justify-end" :class="modalName == 'drawerModalR' ? 'show' : 'hide'" @click="hideModal">
			<view class="cu-dialog basis-lg" @click.stop :style='drawerStyle'>
				<view class="cu-list menu text-left">
					<view class="cu-item arrow" v-for="(item, index) in 5" v-key>
						<view class="content">
							<view>Item {{index + 1}}</view>
						</view>
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
				modalName: '',
				checkbox: [{
					value: 0,
					name: '10元',
					checked: false,
					hot: false,
				}, {
					value: 1,
					name: '20元',
					checked: true,
					hot: false,
				}, {
					value: 2,
					name: '30元',
					checked: true,
					hot: true,
				}, {
					value: 3,
					name: '60元',
					checked: false,
					hot: true,
				}, {
					value: 4,
					name: '80元',
					checked: false,
					hot: false,
				}, {
					value: 5,
					name: '100元',
					checked: false,
					hot: false,
				}],
				CustomBar: this.CustomBar
			}
		},
		computed: {
			drawerStyle() {
				var Custom = this.CustomBar
				var style = `top: ${Custom}px;height:calc${(1350 - Custom)}px`
				return style
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
			},
			chooseCheckbox(e) {
				let that = this
				let items = that.checkbox
				let values = e.currentTarget.dataset.value
				for (let i = 0; i < items.length; i ++) {
					if (items[i].value == values) {
						items[i].checked = !items[i].checked;
						break
					}
				}
				that.checkbox = items
			}
		}
	}
</script>

<style>

</style>
