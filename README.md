## simple-webpack  
[webpack起步](http://zhaoda.net/webpack-handbook/amd.html) 
### 安装
`$ npm install webpack -g
$ npm install webpack --save-dev
$ npm install webpack-dev-server --save-dev
`
### 使用  
`$ webpack entry.js bundle.js`
在根目录创建 package.json 来添加 webpack 需要的依赖：

`{
  "name": "webpack-example",
  "version": "1.0.0",
  "description": "A simple webpack example.",
  "main": "bundle.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [
    "webpack"
  ],
  "author": "zhaoda",
  "license": "MIT",
  "devDependencies": {
    "css-loader": "^0.21.0",
    "style-loader": "^0.13.0",
    "webpack": "^1.12.2"
  }
}`
然后创建一个配置文件 webpack.config.js：

`var webpack = require('webpack')

module.exports = {
  entry: './entry.js',
  output: {
    path: __dirname,
    filename: 'bundle.js'
  },
  module: {
    loaders: [
      {test: /\.css$/, loader: 'style-loader!css-loader'}
    ]
  }
}`

当项目逐渐变大，webpack 的编译时间会变长，可以通过参数让编译的输出内容带有进度和颜色。

`$ webpack --progress --colors`
如果不想每次修改模块后都重新编译，那么可以启动监听模式。开启监听模式后，没有变化的模块会在编译后缓存到内存中，而不会每次都被重新编译，所以监听模式的整体速度是很快的。

`$ webpack --progress --colors --watch`
当然，使用 webpack-dev-server 开发服务是一个更好的选择。它将在 localhost:8080 启动一个 express 静态资源 web 服务器，并且会以监听模式自动运行 webpack，在浏览器打开 http://localhost:8080/ 或 http://localhost:8080/webpack-dev-server/ 可以浏览项目中的页面和编译后的资源输出，并且通过一个 socket.io 服务实时监听它们的变化并自动刷新页面。

### 安装
$ npm install webpack-dev-server -g

### 运行
`$ webpack-dev-server --progress --colors`
[webpack 详解](http://www.cnblogs.com/vajoy/p/4650467.html)  

