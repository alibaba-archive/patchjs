## Loader

### Reference

```html
<script src="./patchjs-loader/2.0.0/websqldb.js"></script>
<script src="./patchjs-loader/2.0.0/index.js"></script>
```

### API 

```js
patchjs.config({
  path: 'http://static.domain.com/path/to/',
  cache: true,
  increment: true,
  version: '0.1.0'
}).load('index.css').load('common.js').wait().load('index.js', function (url, fromCache) {
  // fromCache 
});
```

## Nginx Configure

```bash
location /static/css/ {
    patchjs on;
    patchjs_max_file_size 1024;
}
    
location /static/js/ {
    patchjs on;
    patchjs_max_file_size 1024;
}
```


## Webpack Plugin

```js
var path = require('path');
var PatchjsWebpackPlugin = require('patchjs-webpack-plugin');

module.exports = {
  entry: {
    index: './index.js'
  },
  output: {
    path: path.join(__dirname, 'dist'),
    filename: '[name].js'
  },
  module: {
    loaders: [
      { test: /\.css$/, loader: 'style-loader!css-loader' }
    ]
  },
  plugins: [
    new PatchjsWebpackPlugin({increment: true})
  ]
};
```
