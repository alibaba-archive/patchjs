## Site

https://patchjs.github.io/

## View on Github

https://github.com/patchjs

## Key Future

* simple and easy to use API, like Labjs.

* support localStorage / Web SQL Database.

* real time diff compute through nginx.

* build diff compute through webpack.


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

[More](https://github.com/patchjs/patchjs-loader)


## Nginx Configure

```bash
location /static/ {
    patchjs on;
    patchjs_max_file_size 1024;
}
```

[More](https://github.com/patchjs/patchjs-nginx-module)


## Webpack Configure

```js
var PatchjsWebpackPlugin = require('patchjs-webpack-plugin');

module.exports = {
  plugins: [
    new PatchjsWebpackPlugin({
      increment: true,
      path: 'http://static.domain.com/path/to/'
    })
  ]
};
```

[More](https://github.com/patchjs/patchjs-webpack-plugin)



