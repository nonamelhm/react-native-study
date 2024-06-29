# react-native学习
> react-native学习实操过程以及笔记，便于温故

- [中文官网](https://reactnative.cn/)
- [学习视频](https://www.bilibili.com/video/BV1Pt4y1n7bD?p=1&vd_source=4046650f4b6e75ab86067f7a5a418626)


## 基本环境搭建
* 安装node.js 
  * node.js的版本应该>=12(推荐使用LTS稳定版本)
  * 推荐使用国内镜像源(推荐安装nrm 便于命令切换镜像源 `nrm use taobao`)
   ```shell
     npm config set registry https://registry.npm.taobao.org
   ```
  * 推荐使用nvm安装便于切换node.js版本号
* 安装yarn(毕竟yarn react-native都是facebook出品)
* 安装react-native脚手架
  ```shell
   npm  install -g react-native-cli
   ```

**注意：**
* windows只能安装安卓环境
* mac可以安装安卓环境以及ios环境

## 搭建安卓环境
1. 安装JDK
   * [下载JDK(Java SE Development Kit)](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
   * JDK的版本必须是 1.8(1.8版本，官方也直接称8版本)
     * 目前不支持高于 1.8的 JDK版本
   * 下载时要求登陆(请先注册 oracle 账号)或者直接找老师，获取上面的安装包
   * 安装JDK(一直“下一步”)
     * 命令行中，输入java-version，验证安装是否成功
2. 安装Android Studio

3. 安装Android SDK
4. 配置环境变量
