# 安装命令 npm i vue-countup-v3

> 参考文档 https://www.jb51.net/javascript/303173xyw.htm#_label5
> github 地址 https://github.com/jizai1125/vue-countup-v3/#readme

> 滚动器翻牌效果 https://www.npmjs.com/package/odometer_countup
> ts 使用

```
<script setup lang="ts">
  import { ref } from 'vue'
  import CountUp from 'vue-countup-v3'
  import type { ICountUp, CountUpOptions } from 'vue-countup-v3'

  const endValueRef = ref(2022.22)
  // coutup.js options
  const options: CountUpOptions = {
    separator: '❤️'
    // ...
  }
  let countUp: ICountUp | undefined
  const onInit = (ctx: ICountUp) => {
    console.log('init', ctx)
    countUp = ctx
  }
  const onFinished = () => {
    console.log('finished')
  }
</script>

<template>
  <count-up
    :end-val="endValueRef"
    :duration="2.5"
    :decimal-places="2"
    :options="options"
    :loop="2"
    :delay="2"
    @init="onInit"
    @finished="onFinished"></count-up>
</template>
```
