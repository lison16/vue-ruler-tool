![标尺辅助线.gif](https://upload-images.jianshu.io/upload_images/12792466-b910b0ac21305c52.gif?imageMogr2/auto-orient/strip)
# v-ruler

---

> 一个基于vue的网页标尺辅助线工具
>
> 在gorkys同学的vue-ruler-tool基础上进行了优化和bug fix


### Feature
- 没有依赖
- 可拖动的辅助线
- 快捷键支持


### Install
```
$ npm install --save v-ruler
```

### Use
```
import Vue from 'vue'
import VRuler from 'v-ruler'

Vue.component('v-ruler', VRuler)
```
你现在就可以使用该组件了
```
<template>
  <div id="app">
    <v-ruler
      :content-layout="{left:200,top:100}"
      :is-scale-revise="true"
      :preset-line="presetLine"
    >
      <div class="test"></div>
    </v-ruler>
  </div>
</template>

<script>
import VRuler from 'v-ruler'
export default {
  name: 'app',
  components:{
    VRuler
  },
  data () {
    return {
      presetLine: [{ type: 'l', site: 100 }, { type: 'v', site: 200 }]
    }
  }
}
</script>
```
### Props
**parent**

类型:`Boolean`

默认值: `false`

限制组件大小在父级内部
```
<v-ruler :parent="true" >
```
**position**

类型:`String`

默认值: `relative`

可能值:`['absolute', 'fixed', 'relative', 'static', 'inherit']`

规定标尺工具的定位类型
```
<v-ruler :position="'fixed'" >
```
**isHotKey**

类型: `Boolean`

默认值: `true`

快捷键键开关，目前仅支持快捷键`R`标尺显示开关
```
<v-ruler :is-hot-key="true" >
```
**visible**

类型: `Boolean`

默认值: `true`

是否显示，如果设为false则隐藏，可通过.sync接收来自`R`快捷键的修改
```
<v-ruler :visible.sync="visible" >

data() {
  return {
    visible: true
  }
}
```
**isScaleRevise**

类型: `Boolean`

默认值: `false`

刻度修正(根据content进行刻度重置),意思就是从内容的位置开始从0计数
```
<v-ruler :is-scale-revise="ture" >
```

**presetLine**

类型: `Array`

默认值: `[]`

接受格式:` [{ type: 'l', site: 50 }, { type: 'v', site: 180 }]`

预置参考线`l`代表水平线，`v`代表垂直线，`site`为Number类型
```
<v-ruler :preset-line="[{ type: 'l', site: 100 }, { type: 'v', site: 200 }]" >
```
**contentLayout**

类型: `Object`

默认值: `{ top: 0, left: 0 }`

内容部分布局分布，及内容摆放位置
```
<v-ruler :content-layout="{left:200,top:100}" >
```
### Methods

**quickGeneration**

参数:`[{ type: 'l', site: 100 }, { type: 'v', site: 200 }]`

快速设置参考线，一般用来通过弹窗让用户输入
```
<v-ruler ref='rulerTool' >
let params=[
        { type: 'l', site: 100 },
        { type: 'v', site: 200 }
]
this.$refs.rulerTool.quickGeneration(params)
```
### 优化项
- [x] 标尺与窗口间距
## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
