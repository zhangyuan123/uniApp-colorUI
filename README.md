# uniApp-colorUI
一款uni-app 同时结合“文晓港”开发的colorUI微信小程序UI组件库

color UI cover by "文晓港"


### uniApp结合colorUI
下载源码解压，复制目录下的 /colorui 文件夹到你的项目根目录

App.vue 引入关键Css main.css icon.css

/*每个页面公共css */

`@import url("colorui/main.css");`

`@import url("colorui/icon.css");`


##### 使用自定义导航栏

自定义导航栏组件可以使开发者更灵活地进行个性化开发

获取系统信息（App.vue）

```
onLaunch: function() {
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
```

取消系统导航栏配置（page.json）

`"navigationStyle": "custom"`

组件已封装，直接在main.js中引入并声明

```
import cuCustom from './colorui/components/cu-custom.vue'

Vue.component('cu-custom',cuCustom)
```

页面直接调用即可

1、显示返回按钮及返回首页图标

```
<cu-custom bgColor='bg-gradual-pink' isCustom='ture'>
  <view slot='content'>操作条</view>
</cu-custom>
```

2、显示返回按钮和返回文字

```
<cu-custom bgColor='bg-gradual-blue' isBack='ture'>
  <view slot='backText'>返回</view>
  <view slot='content'>背景</view>
</cu-custom>
```
