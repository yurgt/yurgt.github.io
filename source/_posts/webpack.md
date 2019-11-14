---
title: webpack
date: 2017-07-26 13:51:48
tags: webpack node
---

# webpack

## 四个概念：
- *entry*
- *output*
- *loaders*
- *plugins*

## entry:

### 用法: 
```
  entry: {
    [entryChunkName: string]: string|Array<string>
  }
```

### 单页应用
```javascript
//webpack.config.js
const config = {
  entry: {
    main: './path/to/my/entry/file.js'
  }
}
module.export = config;
```

### 多页应用
``` javascript
const config = {
  entry: {
    pageOne: './src/pageOne/index.js',
    pageTwo: './src/pageTwo/index.js',
    pageThree: './src/pageThree/index.js'
  }
}
```

## output : 
### 用法 : 
- *filename* 指定打包后输出的文件名
- *path* 指定打包后输出的文件的绝对路径

```javascript
output: {
  filename: 'filename.js',
  path: '/path'
}
```
### 输出文件规范
***打包后文件输出规范由output决定***
```javascript
//全部打包输出成一个文件
const config = {
  entry: {
    app: './src/file.js',
    search: './src/search.js'
  }
  output: {
    filename: bundle.js,
    path: '/home/proj/public/assets'  //假定输出文件路径
  }
}

// 多入口文件
const config = {
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: [name].js,
    path: '/dist',
  }
}
// output: ./dist/app.js, ./dist/search.js
```

### 高级用法
***静态资源使用CDN和hashes***

```javascript
output: {
  path: "/home/proj/cdn/assets/[hash]",
  publicPath: "http://cdn.example.com/assets/[hash]/"
}
// 如果不知道publicPath, 可以删除它，并在入口配置中设置
__webpack_public_path = myRuntimePublicPath
```