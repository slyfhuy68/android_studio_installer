# Android Studio官方安装包 
# 解决Android Studio国内网络问题


作者：**[技术爬爬虾](https://github.com/tech-shrimp/me)** and [slyfhuy68](https://github.com/slyfhuy68) <br>
技术爬爬虾：B站，抖音，Youtube全网同名，转载请注明作者<br>

## Android Studio 安装
下载地址：[Releases](https://github.com/slyfhuy68/android_studio_installer/releases)
## Gradle安装失败
解决方法：在[Gradle Releases](https://github.com/gradle/gradle-distributions/releases)手动下载<br>
位置:`%USERPROFILE%\.gradle\wrapper\dists\`
## 汉化
Android Studio 是基于IntelliJ IDEA的,因此IDEA的汉化包是可以直接用到Android Studio上.<br>
1.[语言包](https://plugins.jetbrains.com/plugin/13710-chinese-simplified-language-pack----/versions)Compatibility Range是支持版本,下载后解压出lib\zh.XXX.XX.jar <br>
2.点击左侧的Plugins,点击Installed旁边的设置图标,选择InstallPlugin from Disk <br>
4.找到刚才解压的zh.XXX.XX.jar 安装 <br>
5.在Customize中切换语言，重启android studio<br>
## Your Android SDK is missing, out of date or corrupted.
某博客提供的地址：https://dl.google.com/android/repository/repository2-1.xml<br>
android repository：https://dl.google.com/android/repository/repository2-3.xml<br>
android repository v2：https://dl.google.com/android/repository/repository2-2.xml<br>
http://dl-ssl.google.com/android/repository/XXXXXXXX.zip
http://dl.google.com/android/repository/XXXXXXXX.zip
## Plugin [id: 'com.android.application', version: '8.7.3', apply: false] was not found in any of the following sources:
试了一下阿里镜像仓库最新版本是"8.2.0-alpha04"没有8.7.3版本<br>
可以搭建一个本地仓库<br>
`https://dl.google.com/dl/android/maven2/google/com/android/application/com.android.application.gradle.plugin/<version>/com.android.application.gradle.plugin-<version>.pom`<br>
`https://dl.google.com/dl/android/maven2/google/com/android/application/com.android.application.gradle.plugin/maven-metadata.xml`<br>
`https://dl.google.com/dl/android/maven2/google/`是前缀<br>
settings.gradle的url填`file:///D:/path/to/maven/`
Releases里有示例仓库

