React笔记整理
ctrl alt + T  打开命令行窗口

  linux系统开始想装上 git 和curl 工具
	sudo apt-get install git curl  安装 git 和 curl (curl 类似传输服务的一个软件)
	要用超级管理员权限运行  sudo

	命令
		mkdir 新建文件夹
		cd  进入文件夹
		ls  显示 当前目录下的文件及文件目录  参数 -a  显示隐藏文件
		rm  删除文件  删除文件夹要加 -rf参数



	git命令  

		git clone 远程仓库地址



===================================================================================
	在本地新建一个文件夹  demo

		进入这个文件夹   cd demo

		1 git init   初始化为git仓库

		2 在本地仓库中创建文件  修改文件

		3 git status   查看仓库当前状态（就是说你对哪些文件做了修改）

		4 git add -A   添加所有文件到暂存区

		5 git commit -m "版本留言"   做成一个版本

		6 在github上创建一个与本地仓库同名的空的远端仓库（不勾选readme.md）   复制仓库地址

		7 git remote add origin 仓库地址   将远端的仓库地址添加到版本中  以后push的时候就不用每次都加 网址了。

		8 git push -u origin master   将本地的版本推送到远端仓库

		如果是从远端克隆下来的仓库  6 7 可省略   在commit 做成版本之后  直接  git push 推送就可以了


-------	如果提交的仓库地址错误：

		change remote address
		atom .git/config
	delete all remote address settings, 删掉配置信息里的  错误地址
	and run git remote add again  再次 git remote add origin 仓库地址



===================================================================

	git的分支操作

		git branch 分支名		创建分支

		git checkout 分支名		切换分支

		git branch 			查看当前分支

		git merge 分支名		合并某分支到当前分支

		git branch -d <name>	删除分支

		git checkout -b <name>	创建并切换到当前分支



git push -u origin gh-pages   将新的分支push到远端的分支上  要加 -u origin  分支名

修改主分支的内容，切换到  gh-pages分支  将主分支的修改   同步到  gh-pages分支上

	git pull origin master









===============================================================


	linux 先安装 nvm  -- 用来安装nodejs的工具  可以安装多个版本node
		github上搜索nvm  从上边找到  安装命令代码  

		curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.31.2/install.sh | bash
		粘贴到命令行   回车
		完成之后重启命令行

	安装node

	查看有哪些版本可以安装

		nvm ls-remote

	安装版本 v6.2.2

		nvm install v6.2.2


	设置默认 node 版本

	利用 nvm 可以在我们的机器上安装多个版本 node ，并且可以进行灵活的切换。下面将 5.10.1 这个 node 版本设置为默认。执行下面语句即可。重启 shell 之后，执行 node -v 可以查看当前的 node 版本。

		nvm alias defaule 5.10.1




		===gulp

		全局安装gulp   npm install gulp -g

		在项目中安装gulp     npm install gulp --save   一定要加save
		安装gulp-wrap插件   npm install gulp-wrap --save


		配置gulpfilejs



		deprecated   过期的包

		obsolete    作废的包


================================================================


bable 环境配置

	安装babel
		项目内安装   npm install babel-cli --save-dev
		全局安装    npm install babel-cli -g


	编译js代码

		babel index.js -o after.js    -o 是输出编译文件，将index.js 编译成 after.js

		babel src -d build   -d参数是编译整个目录  将src目录下的所有js文件编译输出到 build 文件夹




webpack配置babel编译 es6语法

	进入项目目录   cd webpack-babel

	npm init   初始化项目 会创建一个package.json

	nip i -D webpack   安装webpack

	touch  webpack.config.js  配置信息如下：
  ```
  var path = require('path');

  module.exports = {
    entry: path.resolve(__dirname, 'src/index.js'),
    output: {
      path: path.resolve(__dirname, 'build'),
      filename: 'bundle.js'
    },
    module: {
      loaders: [
    {
      test: /\.js$/,
      loader: 'babel-loader'
    }
      ]
    }
  };

安装npm包  babel-core  babel-loader   babel-preset-es2015  babel-preset-stage-0


创建 .babelrc  配置文件

{
   "presets": ["es2015","stage-0"],
   "plugins": []
}


src目录下写源代码
src
 |
 -----index.js


编译代码   ./node_modules/.bin/webpack

  ```
