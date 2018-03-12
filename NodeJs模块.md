# path
* path 模块提供了一些工具函数，用于处理文件与目录的路径。可以通过以下方式使用：
### 1. path.join
* 使用平台特定的分隔符把全部给定的 path 片段连接到一起，并规范化生成的路径。
```
const path = require('path');

path.join('/foo', 'bar', 'baz/asdf', 'quux', '..');
// 返回: '/foo/bar/baz/asdf'
```
### 2.path.parse(path)
* path.parse() 方法返回一个对象，对象的属性表示 path 的元素。 尾部文件分隔符会被忽略
* `dir <string>`
* `root <string>`
* `base <string>`
* `name <string>`
* `ext <string>`

```
path.parse('/home/user/dir/file.txt');
// 返回:
// { root: '/',
//   dir: '/home/user/dir',
//   base: 'file.txt',
//   ext: '.txt',
//   name: 'file' }
```
# fs (文件系统)
* 文件 I/O 是对标准 POSIX 函数的简单封装。 通过 require('fs') 使用该模块。 所有的方法都有异步和同步的形式。
### 1. fs.writeFile(file, data[, options], callback)
* `file <string> | <Buffer> | <integer>` 文件名或文件描述符
* `data <string> | <Buffer> | <Uint8Array>`
* `options <Object> | <string>`
  - `encoding <string> | <null>` 默认 = 'utf8'
  - `mode <integer>` 默认 = 0o666
  - `flag <string>` 默认 = 'w'
* `callback <Function>`
  - `err <Error>`
```
fs.writeFile('message.txt', 'Hello Node.js',function(err,data){
    if(err){
        throw err;
    }
    console.log(data);
});
```
### 2.fs.readFile(path[, options], callback)

* `path <string> | <Buffer> | <URL> | <integer> `
文件名或文件描述符。
* `options <Object> | <string>`
  - `encoding <string> | <null>` 默认为 null。
  - `flag <string>` 默认为 'r'。
* `callback <Function>`
  - `err <Error>`
  - `data <string> | <Buffer>`

# HTTP
### 1.setHeader
```
request.setHeader('Content-Type', 'application/json');
```
### 2.http.createServer
* 创建服务
```
const http = require('http');
let server=http.createServer(function(res,req){
    
})
server.listen(8080);
```
### 3.server.listen()
* 监听端口
```
server.listen(8080);
```
# URL
### 1.url.parse(urlString[, parseQueryString[, slashesDenoteHost]])
* `urlString <string>` 要解析的 URL 字符串。
* `parseQueryString <boolean>` 如果为 true，则 query 属性总会通过 querystring 模块的 parse() 方法生成一个对象。 如果为 false，则返回的 URL     对象上的 query 属性会是一个未解析、未解码的字符串。 默认为 false。
* `slashesDenoteHost <boolean>` 如果为 true，则 // 之后至下一个 / 之前的字符串会被解析作为 host。 例如，//foo/bar 会被解析为 {host: 'foo', pathname: '/bar'} 而不是 {pathname: '//foo/bar'}。 默认为 false。
* `url.parse()` 方法会解析一个 URL 字符串并返回一个 URL 对象。
```
var str = 'http://www.baidu.com?user=wangpeiqing';
console.log(url_.parse(str, true));
//  Url {
//   protocol: 'http:',
//   slashes: true,
//   auth: null,
//   host: 'www.baidu.com',
//   port: null,
//   hostname: 'www.baidu.com',
//   hash: null,
//   search: '?user=wangpeiqing',
//   query: { user: 'wangpeiqing' },
//   pathname: '/',
//   path: '/?user=wangpeiqing',
//   href: 'http://www.baidu.com/?user=wangpeiqing' 
//  }

```