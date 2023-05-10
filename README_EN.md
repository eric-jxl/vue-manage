# vue-manage-system

<a href="https://github.com/vuejs/vue">
    <img src="https://img.shields.io/badge/vue-2.6.10-brightgreen.svg" alt="vue">
  </a>
  <a href="https://github.com/ElemeFE/element">
    <img src="https://img.shields.io/badge/element--ui-2.8.2-brightgreen.svg" alt="element-ui">
  </a>
  <a href="https://github.com/lin-xin/vue-manage-system/blob/master/LICENSE">
    <img src="https://img.shields.io/github/license/mashape/apistatus.svg" alt="license">
  </a>
  <a href="https://github.com/lin-xin/vue-manage-system/releases">
    <img src="https://img.shields.io/github/release/lin-xin/vue-manage-system.svg" alt="GitHub release">
  </a>


The web management system solution based on Vue3 and ElementPlus。[live demo](https://lin-xin.gitee.io/example/work/)

Please check the version of vue2 in [tag V4.2.0](https://github.com/lin-xin/vue-manage-system/tree/V4.2.0)



## Preface

The scheme as a set of multi-function background frame templates, suitable for most of the WEB management system development. Convenient development fast simple good components based on Vue3 and ElementPlus. Color separation of color style, support manual switch themes, and it is convenient to use a custom theme color.

## Function

-   [x] Element-UI
-   [x] Login/Logout
-   [x] Dashboard
-   [x] Table
-   [x] Tabs
-   [x] From
-   [x] Chart :bar_chart:
-   [x] Editor
-   [x] Markdown
-   [x] Upload pictures by clipping or dragging
-   [x] Permission
-   [x] Three level menu
-   [x] Custom icon

## Installation steps

    git clone https://github.com/lin-xin/vue-manage-system.git		// Clone templates
    cd vue-manage-system											// Enter template directory
    npm install													// Installation dependency

## Local development

    npm run dev

## Constructing production

    npm run build

## Component description and presentation

### vue-schart

Vue.js wrapper for sChart.js. Github : [vue-schart](https://github.com/lin-xin/vue-schart#/)

```html
<template>
    <div>
        <schart class="wrapper" canvasId="myCanvas" :options="options"></schart>
    </div>
</template>
<script setup>
import { ref } from 'vue';
import Schart from "vue-schart"; // 导入Schart组件
const options = ref({
    type: "bar",
    title: {
        text: "最近一周各品类销售图",
    },
    labels: ["周一", "周二", "周三", "周四", "周五"],
    datasets: [
        {
            label: "家电",
            data: [234, 278, 270, 190, 230],
        },
        {
            label: "百货",
            data: [164, 178, 190, 135, 160],
        },
        {
            label: "食品",
            data: [144, 198, 150, 235, 120],
        },
    ],
})
</script>
<style>
    .wrapper {
        width: 7rem;
        height: 5rem;
    }
</style>
```

## Screenshot

### Default theme

![Image text](https://github.com/lin-xin/manage-system/raw/master/screenshots/wms1.png)


## License

[MIT](https://github.com/lin-xin/vue-manage-system/blob/master/LICENSE)

## Thanks

Special thanks to [JetBrains](https://www.jetbrains.com/) for providing free [WebStorm](https://www.jetbrains.com/webstorm/) authorization for open source projects

![WebStorm](https://resources.jetbrains.com/storage/products/company/brand/logos/WebStorm_icon.svg?_gl=1*1442hrc*_ga*NzI3Njc2MDA2LjE2ODE0MDE2NDc.*_ga_9J976DJZ68*MTY4MTg2NzY1Mi4yLjEuMTY4MTg3MDk4OC4zMC4wLjA.)