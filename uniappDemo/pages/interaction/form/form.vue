<template>
	<view class="content">
		<cu-custom bgColor='bg-gradual-pink' isBack='ture'>
			<view slot='backText'>返回</view>
			<view slot='content'>表单</view>
		</cu-custom>
		<form>
			<view class="cu-form-group margin-top">
				<view class="title">邮件</view>
				<input type="text" placeholder="两字短标题">
			</view>
			<view class="cu-form-group">
				<view class="title">输入框</view>
				<input type="text" placeholder="三字标题">
			</view>
			<view class="cu-form-group">
				<view class="title">收货地址</view>
				<input type="text" placeholder="统一标题的宽度">
			</view>
			<view class="cu-form-group">
				<view class="title">收货地址</view>
				<input type="text" placeholder="输入框带个图标">
				<text class="cuIcon-locationfill text-orange"></text>
			</view>
			<view class="cu-form-group">
				<view class="title">验证码</view>
				<input type="text" placeholder="输入框带个按钮">
				<button class="cu-btn bg-green shadow">验证码</button>
			</view>
			<view class="cu-form-group">
				<view class="title">手机号码</view>
				<input type="text" placeholder="输入框带标签">
				<view class="cu-capsule radius">
					<view class="cu-tag bg-blue">+86</view>
					<view class="cu-tag line-blue">中国大陆</view>
				</view>
			</view>
			<view class="cu-form-group margin-top">
				<view class="title">普通选择</view>
				<picker :range="picker" :value="index" @change="pickerChange">
					<view class="picker">{{index?picker[index]:'禁止换行，超出容器部分会以 ... 方式截断'}}</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">多列选择</view>
				<picker mode="multiSelector" :range="multiArray" :value="multiIndex" @change="multiChange" @columnchange="multiColumnChange">
					<view class="picker">{{multiArray[0][multiIndex[0]]}}，{{multiArray[1][multiIndex[1]]}}，{{multiArray[2][multiIndex[2]]}}</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">时间选择</view>
				<picker mode="time" :value="time" start="13:43" end="24:00" @change='timeChange'>
					<view class="picker">{{time}}</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">日期选择</view>
				<picker mode="date" :value="date" start="2015-09-01" end="2020-09-01" @change="dateChange">
					<view class="picker">{{date}}</view>
				</picker>
			</view>
			<view class="cu-form-group">
				<view class="title">地址选择</view>
				<picker mode="region" :value="region" @change="regionChange">
					<view class="picker">{{region[0]}}，{{region[1]}}，{{region[2]}}</view>
				</picker>
			</view>
			<view class="cu-form-group margin-top">
				<view class="title">开关选择</view>
				<switch />
			</view>
			<view class="cu-form-group">
				<view class="title">定义颜色</view>
				<switch checked class="red sm" />
			</view>
			<view class="cu-form-group">
				<view class="title">定义图标</view>
				<switch checked class="switch-sex" />
			</view>
			<radio-group class="block">
				<view class="cu-form-group">
					<view class="title">方形开关</view>
					<switch checked class="orange radius sm" />
				</view>
				<view class="cu-form-group margin-top">
					<view class="title">单选操作(radio)</view>
					<radio checked></radio>
				</view>
				<view class="cu-form-group">
					<view class="title">定义样式</view>
					<radio class="radio"></radio>
				</view>
				<view class="cu-form-group">
					<view class="title">定义颜色</view>
					<view>
						<radio class="blue radio"></radio>
						<radio class="red margin-left-sm"></radio>
					</view>
				</view>
			</radio-group>
			<view class="cu-form-group margin-top">
				<view class="title">复选框操作(checked)</view>
				<label class="checkbox">
					<checkbox />
				</label>
			</view>
			<view class="cu-form-group">
				<view class="title">定义形状</view>
				<label class="checkbox">
					<checkbox checked class="round" />
				</label>
			</view>
			<view class="cu-form-group">
				<view class="title">定义颜色</view>
				<label class="checkbox">
					<checkbox checked class="round blue" />
				</label>
			</view>
			<view class="cu-bar bg-white margin-top">
				<view class="action">图片上传</view>
				<view class="action">{{imgList.length}}/4</view>
			</view>
			<view class="cu-form-group">
				<view class="grid col-4 grid-square flex-sub">
					<view class="bg-img" v-for="(item, index) in imgList" v-key :data-url='item' @click="viewImage">
						<image :src="item" mode="aspectFill"></image>
						<view class="cu-tag bg-red" :data-index='index' @click.stop="delImg">
							<text class="cuIcon-close"></text>
						</view>
					</view>
					<view class="solids" @click="chooseImg" v-if='imgList.length < 4'>
						<text class="cuIcon-cameraadd"></text>
					</view>
				</view>
			</view>
			<view class="cu-form-group margin-top">
				<view class="title">头像</view>
				<view class="cu-avatar radius bg-gray"></view>
			</view>
			<view class="cu-form-group margin-top">
				<textarea maxlength="-1" placeholder="多行文本输入框" :disabled='modalName != null' :value='textareaAValue' @input="textareaAInput" />
			</view>
			<view class="cu-form-group align-start">
				<view class="title">文本框</view>
				<textarea maxlength="-1" placeholder="多行文本输入框" :disabled='modalName != null' :value='textareaBValue' @input="textareaBInput" />
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				index: null,
				picker: ['喵喵喵', '汪汪汪', '哼唧哼唧'],
				multiIndex: [0, 0, 0],
				multiArray: [
					['无脊柱动物', '脊柱动物'],
					['扁性动物', '线形动物', '环节动物', '软体动物', '节肢动物'],
					['猪肉绦虫', '吸血虫']
				],
				time: '12:00',
				date: '2020-03-02',
				region: ['河北省', '廊坊市', '固安县'],
				imgList: [],
				modalName: null,
				textareaAValue: '',
				textareaBValue: ''
			}
		},
		methods: {
			pickerChange(e) {
				let that = this
				that.index = e.detail.value
			},
			multiChange(e) {
				let that = this
				that.multiIndex = e.detail.value
			},
			multiColumnChange(e) {
				let that = this
				let data = {
					multiArray: that.multiArray,
					multiIndex: that.multiIndex
				};
				data.multiIndex[e.detail.column] = e.detail.value;
				switch (e.detail.column) {
					case 0:
						switch (data.multiIndex[0]) {
							case 0:
								data.multiArray[1] = ['扁性动物', '线形动物', '环节动物', '软体动物', '节肢动物'];
								data.multiArray[2] = ['猪肉绦虫', '吸血虫'];
								break;
							case 1:
								data.multiArray[1] = ['鱼', '两栖动物', '爬行动物'];
								data.multiArray[2] = ['鲫鱼', '带鱼'];
								break;
						}
						data.multiIndex.splice(1, 1, 0)
						data.multiIndex.splice(2, 1, 0)
						break;
					case 1:
						switch (data.multiIndex[0]) {
							case 0:
								switch (data.multiIndex[1]) {
									case 0:
										data.multiArray[2] = ['猪肉绦虫', '吸血虫'];
										break;
									case 1:
										data.multiArray[2] = ['蛔虫'];
										break;
									case 2:
										data.multiArray[2] = ['蚂蚁', '蚂蟥'];
										break;
									case 3:
										data.multiArray[2] = ['河蚌', '蜗牛', '蛞蝓'];
										break;
									case 4:
										data.multiArray[2] = ['昆虫', '甲壳动物', '蛛形动物', '多足动物'];
										break;
								}
								break;
							case 1:
								switch (data.multiIndex[1]) {
									case 0:
										data.multiArray[2] = ['鲫鱼', '带鱼'];
										break;
									case 1:
										data.multiArray[2] = ['青蛙', '娃娃鱼'];
										break;
									case 2:
										data.multiArray[2] = ['蜥蜴', '龟', '壁虎'];
										break;
								}
								break;
						}
						data.multiIndex.splice(2, 1, 0)
						break;
				}
				that.multiArray = data.multiArray
				that.multiIndex = data.multiIndex
			},
			timeChange(e) {
				let that = this
				that.time = e.detail.value
			},
			dateChange(e) {
				let that = this
				that.date = e.detail.value
			},
			regionChange(e) {
				let that = this
				that.region = e.detail.value
			},
			chooseImg() {
				let that = this
				uni.chooseImage({
					count: 4, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album'], //从相册选择
					success: function(res) {
						if (that.imgList.length != 0) {
							that.imgList = that.imgList.concat(res.tempFilePaths)
						} else {
							that.imgList = res.tempFilePaths
						}
					}
				});
			},
			viewImage(e) {
				let that = this
				console.log(e.currentTarget.dataset.url)
				uni.previewImage({
					urls: that.imgList,
					current: e.currentTarget.dataset.url,
					longPressActions: {
						itemList: ['发送给朋友', '保存图片', '收藏'],
						success: function(data) {
							console.log('选中了第' + (data.tapIndex + 1) + '个按钮,第' + (data.index + 1) + '张图片');
						},
						fail: function(err) {
							console.log(err.errMsg);
						}
					}
				})
			},
			delImg(e) {
				let that = this
				uni.showModal({
					title: '召唤师',
					content: '确定要删除这段回忆吗？',
					cancelText: '再看看',
					confirmText: '再见',
					success: res => {
						if (res.confirm) {
							that.imgList.splice(e.currentTarget.dataset.index, 1);
						}
					}
				})
			},
			textareaAInput(e) {
				let that = this
				that.textareaAValue = e.detail.value
			},
			textareaBInput(e) {
				let that = this
				that.textareaBValue = e.detail.value
			}
		}
	}
</script>

<style>

</style>
