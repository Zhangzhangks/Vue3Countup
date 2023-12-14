<template>
  <div class="zks">
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>
    <h1>111</h1>

  </div>
  <CountUp :end-val="endValueRef" :loop="2" :delay="0" @init="onInit" @finished="onFinished" :autoplay="false"
    :options="options">
    <template #prefix>
      <span style="color: orange">prefix</span>
    </template>
    <template #suffix>
      <span style="color: red">prefix</span>
    </template>
  </CountUp>


  <button @click="onReset">开始</button>
  <button @click="pause">切换</button>
  <button @click="Onrefresh">重置数值</button>
  <button @click="update">修改数值</button>
</template>
<script setup lang="js">
import axios from 'axios'

import { ref } from 'vue'
import CountUp from 'vue-countup-v3'


const endValueRef = ref(getRandom())

function getRandom() {
  return Math.random() * 1000000;
}
let countUp = undefined;
// coutup.js options
const options = {
  separator: '★',
  startVal: 10, // number to start at (0) 开始数值，默认 0
  decimalPlaces: 1, // number of decimal places (0) 小数点 位数
  duration: 5, // animation duration in seconds (2) 动画时长
  useGrouping: true,// example: 1,000 vs 1000 (true) 是否使用千分位
  useEasing: true,	//是否开启数字增加过程中的缓动方式
  // easing function for animation(easeOutExpo) 动画函数

  // easingFn: function (t, b, c, d) {
  //   t /= d;
  //   return c * t * t + b;
  // },
  //   // 如果你想使用自定义的缓动函数，可以传递一个函数作为 easingFn
  //   ，该函数接受四个参数：时间（elapsed）、当前值（startVal）、要改变的值（endVal）、持续时间（duration）。
  // 在这个函数中，你可以根据自己的需求实现更加个性化的缓动效果。例如，以下是一个简单的自定义缓动函数：



  // 格式化  用了这个前缀后缀就没用了
  // formattingFn: (n: number) => {
  //   return n + '格式化'
  // },
  // 前缀数字
  prefix: '￥',
  suffix: 'RMB',
  // numerals: ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j'], // numeral glyph substitution 数字符号替换 0 - 9，例如替换为 [a,b,c,d,e,f,g,h,i,j]
  enableScrollSpy: true, // start animation when target is in view 在可视范围内才开始动画// ...
  scrollSpyDelay: 1000,
  onCompleteCallback: () => {
    console.log('callback');
  }, // 结束回调函数
  onStartCallback: () => {
    console.log('start'); //开始回掉
  }
}

const onInit = (ctx) => {
  console.log('init', ctx,)
  countUp = ctx

}
const onFinished = () => {
  console.log('finished')
}


const onReset = () => {
  (countUp).start()
}
const pause = () => {
  countUp && (countUp).pauseResume()
}
const Onrefresh = () => {
  (countUp).reset()
}
const update = () => {
  (countUp).update(getRandom())
}
</script>
<style>
.zks {
  background-color: red;
  height: 2000px;
}
</style>

