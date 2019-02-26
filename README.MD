# 用webpack从0构建vue

## 环境
```
node v10.15.0
npm 6.7.0
```

## 初始化npm
```
npm init -y
```

## 安装vue
```
npm i vue -S
```

## 安装webpack
```
npm i webpack -D
npm i webpack-cli -D
```

## 安装vue-loader
```
npm i vue-loader -D
npm i vue-template-compiler -D // 必须安装
```

## 安装babel-loader
```
npm i babel-loader -D
```

## 安装vue-style-loader
```
npm i vue-style-loader -D
```

## 安装css-loader
```
npm i css-loader -D
```

## 安装html-webpack-plugin
```
npm i html-webpack-plugin -D
```

## package.json
```
"scripts": {
    "start": "webpack --config webpack.config.js"
}
```

## webpack.config.js

```
const VueLoaderPlugin = require('vue-loader/lib/plugin')
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/main.js',
  module: {
    rules: [
      {
        test: /\.vue$/,
        loader: 'vue-loader'
      },
      // 它会应用到普通的 `.js` 文件
      // 以及 `.vue` 文件中的 `<script>` 块
      {
        test: /\.js$/,
        loader: 'babel-loader'
      },
      // 它会应用到普通的 `.css` 文件
      // 以及 `.vue` 文件中的 `<style>` 块
      {
        test: /\.css$/,
        use: [
          'vue-style-loader',
          'css-loader'
        ]
      }
    ]
  },
  plugins: [
    // 请确保引入这个插件！
    new VueLoaderPlugin(),
    new HtmlWebpackPlugin({template: './public/index.html'})
  ]
}
```