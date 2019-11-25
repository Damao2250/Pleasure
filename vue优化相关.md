# 打包优化
1. 路由懒加载
```js
{
  path: '/about',
  name: 'about',
  component: () => import('@/views/about/about'),
},
```

2. 不生成.map 文件
+ webpack默认会生成map文件，map文件是用来调试代码的。此外，这里还要注意sourcemap的配置分 开发（dev）和线上（build）两个地方配置，开发我们就不管了，就用默认的，线上我们是不需要这个代码的。
```js
// 配置 vue.config.js
module.exports = {
  productionSourceMap: false,
}
```

3. Element组件按需加载
```js
// 安装 babel-plugin-component：
npm install babel-plugin-component -D
// 修改babel.config.js
module.exports = {
  presets: [
    [
      '@vue/app',
      {
        useBuiltIns: "entry"
      }
    ]
  ],
  plugins: [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}

```

4. echart优化
```js
// 安装 babel-plugin-equire
npm install babel-plugin-equire -D
// 修改babel.config.js
module.exports = {
  plugins: [
    'equire'
  ],
  // others
}


// 新建echarts.js
const echarts = equire([
  'title',
  'legend',
  'grid',
  'line',
  'bar',
  'pie',
  // others
])
export default echarts



// 或者

// 新建echarts.js
import echarts from 'echarts/lib/echarts'

import 'echarts/lib/chart/line'
import 'echarts/lib/chart/lines'
import 'echarts/lib/chart/radar'
import 'echarts/lib/component/legend'
import 'echarts/lib/component/tooltip'
import 'echarts/lib/component/grid'

export default echarts




// 然后再到需要引用echarts的页面进行引入
import echarts from '../echarts';

```

5. 图片的压缩合并
+ 无损压缩图片：https://tinypng.com/


6. 添加分析工具
```js
// 安装
npm i webpack-bundle-analyzer

// 在 vue.config.js 中添加
module.exports={
  chainWebpack: (config) => {
    /* 添加分析工具 */
    if (process.env.NODE_ENV === 'production') {
      if (process.env.npm_config_report) {
        config.
          plugin('webpack-bundle-analyzer')
          .use(require('webpack-bundle-analyzer').BundleAnalyzerPlugin)
          .end()
        config.plugins.delete('prefetch')
      }
    }
  },
}

// 启动
npm run build --report

```
