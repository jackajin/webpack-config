## babel-loader 
 - 转换es7，es7等新特性语法
 - @babel/core @babel/preset-env babel-loader

webpack.config.js
```
module.exports = {
  ...
  module: {
    rules: [{
      test: '/\.js$/',
      use: 'babel-loader'
    }]
  }
}
```
.babelrc
```
{
  presets: [
    '@babel/preset-evn'
  ] 
}
```
@babel/preset-reat 解析react相关的jsx语法
.babelrc
```
{
  presets: [
    '@babel/preset-env'.
    '@babel/preset-react'
  ]
}
```
## css-loader style-loader less-loader
- less-loader 把less解析成css
- css-loader 加载css，并转换成common.js对象
- style-loader 把css通过style标签插入到html里面的head
```
module.exports = {
  ...
  module: {
    rules: [{
      test: /\.less$/
      use: [
        'style-loader',
        'css-loader',
        'less-loader',
      ]
    }]
  }
}
```
## file-loader url-loader
- file-loader 解析图片，字体资源
- url-loader 解析图片，字体资源, 可以设置小资源base64的转换
```
module.exports = {
  ...
  module: {
    rules: [
      {
        test: /\.(png | jpj | jpej | gif)$/,
        use: [
          'file-loader'
        ]
      },
      {
        test: /.(woff | woff2 | eot | ttf | etf)$/,
        use: [
          'file-loader'
        ]
      },
      {
        test: /\.(png | jpj | jpej | gif)$/,
        use: [{
          loader: 'ure-loader',
          option: {
            limit: 10240 // 10k
          }
        }]
      },
    ]
  }
}
```

## watch 文件监听
 - webpack会轮询判断文件最后编辑的时间是否变化，某个文件发生了变化不会立即告诉监听者，而是缓存起来，等待aggregateTimeout
 ```
 module.exprots = {
  // 默认false，也就是不开启
  watch: true，
  watchOptions: {
    // 默认为空，不监听的文件或者文件夹，支持正则匹配
    ignored: /node_modules/,
    // 监听到变化后会等待300ms再去执行，默认300ms
    aggregateTimout: 300,
    // 判断文件是否变化是不断询问系统指定文件有没有发生变化实现的，默认每秒1000次
    poll: 1000
  }
 }
 ```

