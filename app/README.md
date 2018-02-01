学习地址：http://www.runoob.com/w3cnote/webpack-tutorial.html
webpack 环境安装 cnpm install webpack -g
Webpack 本身只能处理 JavaScript 模块，如果要处理其他类型的文件，就需要使用 loader 进行转换。cnpm install css-loader style-loader
webpack 命令执行后，会默认载入当前目录的 webpack.config.js 文件。
总结：
1.根据模块关系进行静态分析，然后让这些模块按照指定的规则生成对应的静态资源。
2.webpack会给每个模块分配一个唯一的id并通过id索引和访问模块。
3.loader webpack本身只能处理js模块。如果要处理其他类型的文件，就需要使用loader进行转换。
如果我们需要在应用中添加css文件，就需要使用css-loader和style-loader.
css-loader会遍历css文件，然后找到url（）表达式然后处理他们
style-loader会把原来的css代码插入页面中的一个style标签中。
4.require css文件的时候都要写css前缀！styel-loader!css-loader!
5.第二种方式require("./style.css")
webpack runoob1.js bundle.js --module-bind "css=style-loader!css-loader"  注意此处一定要是双引号
6.配置文件
创建webpack.config.js文件。
将一些编译选项放在配置文件中，以便于统一管理。
执行webpack命令即可生成bundle.js文件。
7.插件
插件在webpack的配置信息plugins选项中指定，用于完成写loader不能完成的工作。
webpack内置插件安装命令。 cnpm i webpack --save-dev。
比如我们可以安装内置的 BannerPlugin 插件，用于在文件头部输出一些注释信息。
8.开发环境
当项目逐渐变大，webpack 的编译时间会变长，可以通过参数让编译的输出内容带有进度和颜色。
webpack --progress --colors
如果不想每次修改模块后都重新编译，那么可以启动监听模式。开启监听模式后，没有变化的模块会在编译后缓存到内存中，而不会每次都被重新编译，所以监听模式的整体速度是很快的。
webpack --progress --colors --watch
9.使用 webpack-dev-server 开发服务
通过 localhost:8080 启动一个 express 静态资源 web 服务器，并且会以监听模式自动运行 webpack，在浏览器打开 http://localhost:8080/ 或 http://localhost:8080/webpack-dev-server/ 可以浏览项目中的页面和编译后的资源输出，并且通过一个 socket.io 服务实时监听它们的变化并自动刷新页面。
# 安装
cnpm install webpack-dev-server -g

# 运行
webpack-dev-server --progress --colors