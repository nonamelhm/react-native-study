# react-native学习

> react-native学习实操过程以及笔记，便于温故。主要是需要搭建好ios和安卓环境，然后初始化项目以及打包项目，别的基础还是react

- [中文官网](https://reactnative.cn/)
- [学习视频](https://www.bilibili.com/video/BV1Pt4y1n7bD?p=1&vd_source=4046650f4b6e75ab86067f7a5a418626)
- [UI组件查看(中文官网——组件)](https://reactnative.cn/docs/activityindicator)

## 基本环境搭建

* 安装node.js
    * node.js的版本应该>=12(推荐使用LTS稳定版本)
    * 推荐使用国内镜像源(推荐安装nrm 便于命令切换镜像源 `nrm use taobao`)
   ```shell
     npm config set registry https://registry.npm.taobao.org
   ```
    * 推荐使用nvm安装便于切换node.js版本号
* 安装yarn(毕竟yarn react-native都是facebook出品)
* **安装react-native脚手架**(后续才能用叫脚手架创建项目)
  ```shell
   npm  install -g react-native-cli
   ```

**注意：**

* windows只能安装安卓环境
* mac可以安装安卓环境以及ios环境

## 搭建安卓环境

> 具体配图可查看安装视频

1. 安装JDK
    * [下载JDK(Java SE Development Kit)](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
    * JDK的版本必须是 1.8(1.8版本，官方也直接称8版本)
        * 目前不支持高于 1.8的 JDK版本
    * 下载时要求登陆(请先注册 oracle 账号)或者直接找老师，获取上面的安装包
    * 安装JDK(一直“下一步”)
        * 命令行中，输入java-version，验证安装是否成功
2. 安装Android Studio
    * [下载 Android Studio]( https://developer.android.com/studio/index.html)
    * 安装 Android studio(一直“下一步”)
    * 启动 Android studio
        * 初次启动，需要安装组件(组件约2GB，安装后占用空间约8GB)安装组件的过程巨长巨长巨长，要有耐心
        * 创建项目
3. 安装Android SDK

* What
    * Android SDk 是针对安卓开发的套件
* why
    * 虽然 Android studio 默认会安装最新版本的 Android sDK
    * 但是，目前编译 React Native 应用需要的是 Android 10(a) 版本的 SDK
* HOW
    * 打开 Android studio，在菜单 Tools 下找到"SDK Manager

4. 配置环境变量

* 配置 ANDROID HOME 环境变量
    * 打开 Android Studio，点击菜单 Tools →>SDK Manager，找到 Appearance &Behavior>System Settings -> Android SDK
    * 跟 ANDROID HOME 相关的环境变量
        * %ANDROID HOME%platform-tools
        * %ANDROID HOME%emulator6
        * %ANDROID HOME%tools
        * %ANDROID HOME%ltoolslbin

## 搭建ios环境

1. 安装watchman

```shell
brew install brew
```

2. 安装Xcode（类似android studio)

* react native 目前需要Xcode10或更高版本 可通过app store 下载

3. CocoaPods(类似node.js下面的npm)

```shell
brew install cocoapods
```

## 初始化项目

1. 创建项目

* 初始化项目

> 看起来你遇到了 react-native-cli 的问题，可能是由于 react-native-cli 已被弃用，最新的推荐方法是使用 npx 来创建 React
> Native 项目。

旧：

   ```shell
    react-native init myproject
   ```

现!!:

  ```shell
   npx react-native init MyNewProject
   ```

* 进入项目

   ````shell
   cd myproject
   ````

* 安装依赖

```shell
yarn install
```

**安装依赖踩坑分享**
> 如果yarn install有问题，然后发现没有文件夹yarn.lock,那就新建yarn.lock文件`touch yarn.lock`

* 运行项目
    * Android  `yarn android`
    * IOS  `cd ios && pod install && cd ../`

2. 安装vscode插件

* ES7 React/Redux/GraphQL/React-Native snippets
* [查看快捷命令](https://github.com/r5n-dev/vscode-react-javascript-snippets/blob/HEAD/docs/Snippets.md)

3. 调试工具

* 模拟器调试
    * 模拟器是安装在电脑上的，虚拟的手机界面·模拟器一般跟随 Android studio 和 Xcode 一起安装启动应用，模拟器会一起启动
    * 点击模拟器(使模拟器获取焦点)
    * 快捷键 ctrl+m
    * 点选 debug
    * 自动跳转到浏览器
* 真机调试
    * 打开 USB 调试模式
    * 通过 UsB 线将电脑和手机连起来
    * 启动应用，在手机上安装应用

## 基础知识

1. react语法

* JSx语法·组件(分类，传参，属性，状态)
* 生命周期
* Hook API
* Redux
* 常用安装包

2. StyleSheet

* **RN中的样式与css的不同**
    * 没有继承性
    * RN 中的继承只发生在 Text 组件上样式名采用小驼峰命名
    * fontSize VS font-size
* 所有尺寸都是**没有单位**
    * width: 100
    * 有些特殊的样式名: marginHorizontal(水平外边距)，marginVertical(垂直外边距)

* **RN样式的声明方式**
* 通过 style 属性直接声明
    * 属性值为对象:<组件 style={{样式}}/>
    * 属性值为数组:<组件 style={[{样式1},…, {样式N}]}/>
* 在 style 属性中调用 stylesheet 声明的样式
    * 引入:import {StyleSheet, View } from 'react-native·
    * 声明:const styles=Stylesheet.create({ foo:{样式1}, bar:{样式2} })
    * 使用:<View style={[styles.foo, styles.bar ]}>内容</View>

**代码示例**

```tsx
import React, {Component} from 'react'
import {Text, styleSheet, View} from 'react - native'

export default class App extends component {
    render() {
        return (
            <View style={{marginHorizontal: 20, backgroundColor: '#dfb'}}>
                <Text style={[styles, red, styles, fontlarge]}>Hello RN</Text></View>
        )
    }
}

const styles = stylesheet.create({
    red: {
        color: '#e33'
    },
    fontLarge: {
        fontsize: 40
    }
})
```

3. Flexbox

* Flexbox-术语
    * 容器(container)
        * 采用 Flex 布局的元素，称为 Flex 容器
    * 项目(item)
        * 容器所有子元素，称为 Flex项目(flex item)，简称“项目”
    * 主轴(main axis)
    * 交叉轴(cross axis)

> 因为web端屏幕和手机屏幕问题，RN当中主轴main axis是垂直方向的，方向反过来了。

* **Flexbox-属性**
    * **flexDirection**
        * 声明主轴方向:row(Web默认)|column(RN默认)
    * **justifyContent**
        * 声明项目在主轴上的对齐方式
    * **alignItems**
        * 声明项目在交叉轴上的对齐方式
    * **flex**
        * 声明项目在主轴上的尺寸比例

### 响应式布局

* Flexbox
* Dimensions
    * import { Dimensions }from 'react-native’;
    * const windowWidth = Dimensions.get('window').width;
    * const windowHeight = Dimensions.get('window').height;

**代码示例**

```tsx
import React, {Component} from 'react'
// Dimensions 响应式布局获取屏幕尺寸
import {Text, StyleSheet, View, Dimensions} from 'react-native

export default class index extends Component {
    render() {
        return (
            <View style={[styles.container]}>
                <View style={[styles.itemBase]}>
                    <Text style={[styles.h3]}>扫扫</Text>
                </View>
                <View style={[styles.itemBase]}>
                    <Text style={[styles.h3]}>付款吗</Text>
                </View>
                <View style={[styles.itemBase]}>
                    <Text styie={[styles.h3]}>卡包</Text>
                </View>
                <View style={[styles.itemBase]}>
                    <Text style={[styles.h3]}> 出行</Text>
                </View>
            </View>
        )
    }
}

const styles = StyleSheet.create({
    container: {
        flexDirection: 'row',
        flexWrap: 'wrap'
    },
    itemBase: {
        fjustifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#00b38a',
        width: Dimensions.get('window').width / 3,
        height: 90,
        borderwidth: 1,
        borderColor: 'yellow'
    },
    h3: {
        fontsize: 24
    }
})

```

4. 组件和 API
- 详细了解点击查看[UI组件查看(中文官网——组件)](https://reactnative.cn/docs/activityindicator)

* 简介

> * RN 中的核心组件，是对原生组件的封装
> * 原生组件:Android 或ios 内的组件
> * 核心组件:RN 中最常用的，来自react-native的组件

* 核心组件
    * 基础组件
    * 交互控件
    * 列表视图
    * ios 独有组件
    * Android 独有组件
    * 其他

| 作用   | RN组件(核心组件） | 安卓视图 （原生组件） | iOS视图（原生组件） | HTML视图 |
|------|------------|-------------|-------------|--------|
| 展示区块 | View       | ViewGroup   | UIView      | div    |
| 展示图片 | Image      | ImageView   | UIImageView | img    |
| 展示文本 | Text       | TextView    | UITextView  | p      |
| .... | ....       | ....        | ....        | ....   |

**UI常用核心组件：**

| 组件名               | 描述        |
|-------------------|-----------|
| View              | 视图组件      |
| Text              | 文本组件      | 
| Alert             | 警告框组件     | 
| Button            | 按钮组件      |
| Switch            | 开关组件      | 
| StatusBar         | 状态栏组件     | 
| ActivityIndicator | 加载指示器组件   | 
| TextInput         | 触碰组件(共三个) |
| ScrollView        | 滚动视图组件    | 
| SectionList       | 分组列表组件    | 
| FlatList          | 高性能列表组件   |
| Animated          | 动画组件      |

* 第三方组件
  * 需要单独安装的组件
  * 使用步骤
    * 安装
    * 配置
    * 使用

** 常见的第三方组件**

| 第三方组件名            | 描述       |
|-------------------|----------|
| WebView           | 相当于内置浏览器 |
| Picker            | 下拉框      | 
| Swiper            | 展示轮播效果   | 
| AsyncStorage      | 持久化存储系统  |
| Geolocation       | 获取定位信息   | 
| Camera            | 调用摄像头    |

### 使用WebView第三方组件
> 具体详细使用 查看[官网文档](https://github.com/react-native-webview/react-native-webview)

1. 安装
```shell
yarn add react-native-webview
```
2. 配查
* [官方文档](https://github.com/react-native-webview/react-native-webview)
3. 使用
   * 直接指定 uri 地址
   * 直接渲染 html 代码

### 使用Picker(下拉框)第三方组件
> 具体详细使用 查看[官网文档](https://github.com/react-native-picker/picker)

1. 安装
```shell
yarn add @react-native-picker/picker
```
2. 配置
"https://github.com/react-native-picker/picker
   * 注意:不同版本的配置方式不同
3. 使用
   * 注意平台之间的差异(Android ios)

### 使用(轮播效果)Swiper第三方组件
> 具体详细使用 查看[官网文档](https://github.com/leecade/react-native-swiper)

1. 安装[TY](..%2FTY)
```shell
yarn add react-native-swiper
```
2. 使用
   * https://github.com/leecade/react-native-swiper

### 使用(持久化存储系统)Asyncstorage第三方组件
> 具体详细使用 查看[官网文档](https://github.com/react-native-async-storage/async-storage)

1. 安装
```shell
yarn add @react-native-async-storage/async-storage
```
2. 配置
 * https://github.com/react-native-async-storage/async-storage
3. 使用
 * 增删改查


* 自定义组件

5. 路由与导航


