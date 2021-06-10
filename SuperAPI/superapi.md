## SuperAPI 

 51WORLD SuperAPI是一套由JavaScript语言开发的负责交涉Web页面和云渲染平台之间的编程接口, 基于51云渲染平台使用; 用户可在WEB页面上创建任意HTML5 UI元素, 利用SuperAPI与云场景进行双向交互。

> 参考链接:  http://superapi.51hitech.com/zh/index


## 简易演示示例

> 代码地址: http://superapi.51hitech.com/zh/spadev

```HTML

<template>
  <div id="player" style="display:none;"></div>
  //id="player": 渲染3D场景窗口的Dom节点; 不要在里面加任何自定义开发的元素, 特别是video; 不要使用VUE自身的 v-show;
</template>

<script>
  //引入SuperAPI.js
  import cloudRenderer from "superapi-51world"

  export default {
    name: 'Player',
    data() {
      return {
        cloudRender: null
      }
    },
    created() {
      //初始化实例
      this.cloudRender = new cloudRenderer("player", 0)
      //启动云渲染
      this.cloudRender.SuperAPI("StartRenderCloud", "https://172.31.9.21:8891/a13cf7ff-eed1-489f-e...")
    },
    destroyed() {
      this.cloudRender.SuperAPI("StopRenderCloud") //关闭云渲染, 释放资源 (此处是关键。单页应用释放资源请注意)
    }
  }
</script>
```