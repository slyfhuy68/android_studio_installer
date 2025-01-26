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
1.[语言包](https://plugins.jetbrains.com/plugin/13710-chinese-simplified-language-pack----/versions),Compatibility Range是支持版本,下载后解压出lib\zh.XXX.XX.jar <br>
2.点击左侧的Plugins,点击Installed旁边的设置图标,选择InstallPlugin from Disk <br>
4.找到刚才解压的zh.XXX.XX.jar 安装 <br>
5.在Customize中切换语言，重启Android Studio<br>
## Your Android SDK is missing, out of date or corrupted.
```
猜的地址：
https://dl.google.com/android/repository/repository2-1.xml

Android Repository v2：
https://dl.google.com/android/repository/repository2-2.xml

Android Repository：
https://dl.google.com/android/repository/repository2-3.xml
```
http://dl-ssl.google.com/android/repository/XXXXXXXX.zip 或 http://dl.google.com/android/repository/XXXXXXXX.zip

## Plugin [id: 'com.android.application', version: '8.7.3', apply: false] was not found in any of the following sources:\Could not find com.android.tools.build:gradle:8.7.3.

试了一下阿里镜像仓库，最新版本是"8.2.0-alpha04"没有8.7.3版本<br>
可以搭建一个本地仓库<br>
```
https://dl.google.com/dl/android/maven2/XXX/XXX/XXX/xxxxxx/<version>/xxxxxx-<version>.pom
https://dl.google.com/dl/android/maven2/com/android/application/com.android.application.gradle.plugin/maven-metadata.xml
根目录https://dl.google.com/dl/android/maven2/
```
如果你的仓库的位置是`D:\maven\`
settings.gradle的url就填`file:///D:/maven`(最后不带‘/’带了会报错)<br>
Releases里有示例仓库<br>
把google()注释掉，不然还会从谷歌下载<br>
阿里镜像别删，还有其它的要在阿里镜像仓库下载<br>
## 最终的settings.gradle
```
pluginManagement {
    repositories {
        maven{
            url 'file:///D:/maven'
            content {
                includeGroupByRegex("com\\.android.*")
                includeGroupByRegex("com\\.google.*")
                includeGroupByRegex("androidx.*")
            }
        }
        maven{ url 'https://maven.aliyun.com/repository/google'}
        maven{ url 'https://maven.aliyun.com/repository/gradle-plugin'}
        maven{ url 'https://maven.aliyun.com/repository/public'}
        maven{ url 'https://maven.aliyun.com/repository/jcenter'}
        //google {
        //    content {
        //        includeGroupByRegex("com\\.android.*")
        //        includeGroupByRegex("com\\.google.*")
        //        includeGroupByRegex("androidx.*")
        //    }
        //}
        //google()
        mavenCentral()
        gradlePluginPortal()
    }
}
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        maven{ url 'file:///D:/maven'}
        maven{ url 'https://maven.aliyun.com/repository/google'}
        maven{ url 'https://maven.aliyun.com/repository/gradle-plugin'}
        maven{ url 'https://maven.aliyun.com/repository/public'}
        maven{ url 'https://maven.aliyun.com/repository/jcenter'}
        //google()
        mavenCentral()
    }
}

rootProject.name = "My 1Application"
include ':app'
```
我是一名小学生，有问题欢迎提issues
