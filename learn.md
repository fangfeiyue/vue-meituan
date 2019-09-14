环境准备

```
npx create-nuxt-app meituan
```

打开server目录里的index.js文件，模块使用require方式引入的，一般我们写Vue、React引入组件用的是import，如果我们把`const Koa = require('koa')`换成`import Koa from 'koa'`执行npm run build会报错

安装编译工具

```
npm i babel-cli   // 这是babel解释器的客户端主程序 
npm i babel-core   // babel的核心文件,好像默认会自动安装
npm i babel-preset-es2015 // 把代码转换成ES6
npm i babel-preset-stage-0 // 把代码转换成ES7
```

在根路径创建.babelrc文件，写入配置

```
{
    "presets": ["es2015","stage-0"]
}
```

安装sass相关loader

```
npm i sass-loader node-sass -D
```


书写小技巧

template[v-if] 回车会生成
<template v-if=""></template>



问题

3 errors and 0 warnings potentially fixable with the `--fix` option

修package.json改如下
"lint":"eslint --fix --ext .js,.vue --ignore-path .gitignore ."


