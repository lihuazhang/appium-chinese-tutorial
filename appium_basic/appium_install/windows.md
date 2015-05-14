# Windows 平台

> 主要参考官方对应文档：[running on windows](https://github.com/appium/appium/blob/master/docs/en/appium-setup/running-on-windows.md)

## 局限性

如果你在 windows 上安装 appium ，你没法使用预编译专用于 OS X 的 .app 文件，你也将不能测试 iOS 的应用，因为 appium 依赖 OS X 专用的库来支持 iOS 测试。这意味着你只能通过在 mac 运行 iOS 的应用测试。然而，你也可以通过 `Remote Server` 选项来远程连接你的 mac 执行 iOS 应用测试。

## 开始安装

一共有 3 种安装方式：通过源码安装，通过 npm 安装，通过 AppiumForWindows 安装。但无论使用哪种方式，首先都必须安装依赖库：

1. 安装 [nodejs](http://nodejs.org/download/) v0.10 版本及以上，可通过官方的安装程序来安装。

2. 安装 [android sdk](http://developer.android.com/sdk/index.html)。你可以通过运行 sdk 中 tools 文件夹中的 'android' 程序启动 sdk 管理器，并确保你安装了 Level 17 或以上的版本的 api 。设置 `ANDROID_HOME` 系统变量为你的 Android SDK 路径，并把 tools platform-tools 两个目录加入到系统的 Path 路径里。因为这里面包含有一些执行命令。

3. 安装 java 的 JDK ，并设置 `JAVA_HOME` 环境变量为你的JDK目录。

三种安装方式的优缺点

|安装方式|优点|缺点|安装速度|
|--------|----|----|--------|
|通过源码安装|能方便地修改源代码，能获取未发布版本的最新代码|需要安装的依赖库数量较多|最慢|
|通过 npm 安装|能获取最新版本的代码|需要通过命令行运行，较难实现多版本共存，安装过程|较慢|
|通过 AppiumForWindows 安装|直接解压可用，可以通过换个文件夹的方式直接换版本|所有参数修改都只能在界面上进行|最快|

### 通过源码安装

1. 安装 [Apache Ant](http://ant.apache.org/bindownload.cgi) 
或者直接使用 Android Windows SDK 自带的 ant ，地址在 eclipse\plugins 目录，你需要把这个目录加到你的系统 PATH 变量中

2. 安装 [Apache Maven](http://maven.apache.org/download.cgi) 。 并且设置 M2HOME 和 M2 环境变量，把M2环境变量添加到你的系统PATH变量中。

3. 安装 [Git](http://git-scm.com/download/win) 。 确保你安装了windows下的Git，以便可以运行常用的command命令

现在，你已经下载安装了所有的依赖，运行
    reset.bat
将开始安装。
    
### 通过 npm 安装

运行 `npm install -g appium` 安装 appium （如果没有科学上网，请先[把 npm 换成淘宝源](https://npm.taobao.org)）

### 通过 AppiumForWindows 安装

到 <https://bitbucket.org/appium/appium.app/downloads/> 下载 AppiumForWindows 。解压后即完成安装。


## 运行Appium

要在 windows 上运行测试用例，你需要先启动 Android 模拟器或者连接上一个 API Level 17 以上的android真机。

* 通过源码安装Appium的，请在你所安装的appium目录下执行node.js命令：
```center
node .
```
* 通过 npm 安装的，请在命令行运行`appium`。

* 通过 AppiumForWindows 安装的，请双击打开解压后的文件夹中的 appium.exe ，然后点击界面最后侧的按钮（图标为火箭或者三角形）启动 appium 。

启动成功时，将会有类似以下内容输出，光标停在最后一个空行（里面的版本号根据你使用的 appium 版本会有所不同）：
```
info: Welcome to Appium v1.3.4 (REV c8c79a85fbd6870cd6fc3d66d038a115ebe22efe)
info: Appium REST http interface listener started on 0.0.0.0:4723
info: Console LogLevel: debug

```

## 备注

* 在windows系统下运行 appium.exe 时，需要使用管理员权限；当你通过源码的形式运行 Appium 时，也需要使用管理员权限启动 CMD 。

* 在 windows 系统下运行 Android 项目时，启动Appium时请带上 `--no-reset` 或 `--full-reset` 参数。

* 有一个硬件加速模拟器用于android，但是它有自己的一些限制，如果你想了解更多，请参考[页面](android-hax-emulator.cn.md)

* 确保在你的AVD的 `config.ini` 中有一个配置项为 `hw.battery=yes` 。
