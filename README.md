vue-toast使用说明
===

## 功能说明
<br>
1、支持自定义弹窗文案，并自动计算弹窗的高度调整在屏幕的位置，以一直保持居中<br>
2、支持自定义弹窗显示时长（默认2秒，单位毫秒）<br>
3、支持回调函数，callback将在设定的时间结束后才执行<br>

## 使用方式
<br>
1、将 showToast.vue 文件放置于项目的模板文件夹（个人习惯为 src/components）<br>
2、打开 App.vue，引入vue和showToast组件，并use该组件（其实是use组件里的方法，只不过打包为一个文件了）。<br>

### template部分
<br>
举例，主要就是“<showToast>”那里：<br>
```html
<template>
	<div id="app">
		<router-view></router-view>
		<ShowToast></ShowToast>
	</div>
</template>
```

### script部分
```JavaScript
//引入Vue
import Vue from 'vue'

//引入组件，@cp是我自定义的路径别名，相当于@/components/
import ShowToast from '@cp/showToast.vue'

//注册使用方法
Vue.use(ShowToast)

//添加模板
export default {
	name: 'App',
	components: { ShowToast },
}
```

3、之后在App.vue或者任意子组件里，就可以直接通过 this.$showToast(文案, 显示时间, 回调函数) 去唤起Toast弹窗了。
```JavaScript
//默认2秒的弹窗
this.$showToast("默认2秒的弹窗");

//持续显示10秒的弹窗
this.$showToast("持续显示10秒", 10000);

//执行回调函数
this.$showToast("发布成功，即将进入首页…", 2000, function(){
	this.$router.push({
		name: "home"
	});
});
```

## 其他说明

我使用的是stylus，样式在这里就随便写一下，请根据实际项目需要做调整和本地备份。

附上我的博客原文 http://chengpeiquan.com/article/vue-toast.html