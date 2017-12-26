# serialport_electron_start
> 这是一个基于electron的串口工具桌面应用，因为我在网上走了很多坑，都不成功，终于找到对的方法，编译成功了，这里讲下我的编译成功的方法。

> **完整demo在demo目录中，包括编译好的node_modules，所以有点大**

## 过程
> 这里需要安装python 2.7的环境，记得是2.7，3的话是不行的。

### 安装electron
> 对于可以翻墙的同学用这个

`npm i electron -g`

> 由于下载过慢，所以我采用淘宝的镜像镜像安装cnpm，大家可以自行安装下cnpm，这里就不展开解释了 **下面的操作都采用cnpm**

`cnpm i electron -g`

### 安装electron-prebuilt

`npm install -g electron-prebuilt`

### 安装官方的例子
> 官方文档的例子我就不在这里展开解释了``

> 下载demo

`git clone https://github.com/electron/electron-quick-start.git`

> 安装模块

`cnpm install`

> 安装serialport

`cnpm install --save serialport`

> 安装electron-rebuild, 因为serialport编译的环境是电脑的环境，我们需要重新编译成eletron的环境，所以我们需要electron-rebuild

`npm install --save-dev electron-rebuild`

> 重新编译, 因为当前版本的electron是1.7.10的，所以我们重新把模块编译成适应1.7.10的

`./node_modules/.bin/electron-rebuild -v 1.7.10`

## demo
> 在index.html写我们的demo

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>Hello World!</title>
  </head>
  <body>
    <h1>Hello World!</h1>
    <!-- All of the Node.js APIs are available in this renderer process. -->
    We are using Node.js <script>document.write(process.versions.node)</script>,
    Chromium <script>document.write(process.versions.chrome)</script>,
    and Electron <script>document.write(process.versions.electron)</script>.

    <script>
      // You can also require other files to run in this process
      require('./renderer.js')
      var serialport = require('serialport');

      serialport.list(function(err, ports) {
        console.log(ports);
      });
    </script>
  </body>
</html>
```

## 运行效果
![](https://i.imgur.com/PlgtDdS.png)