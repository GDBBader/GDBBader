---


title: Maven
date: 2021-08-03 16:54:29
tags: [Java,Maven]
type:

---


# Maven介绍

> 在了解Maven之前，我们先来看看一个Java项目需要的东西。首先，我们需要确定引入哪些依赖包。例如，如果我们需要用到[commons logging](https://commons.apache.org/proper/commons-logging/)，我们就必须把commons logging的jar包放入classpath。如果我们还需要[log4j](https://logging.apache.org/log4j/)，就需要把log4j相关的jar包都放到classpath中。这些就是依赖包的管理。


> 其次，我们要确定项目的目录结构。例如，`src`目录存放Java源码，`resources`目录存放配置文件，`bin`目录存放编译生成的`.class`文件。


> 此外，我们还需要配置环境，例如JDK的版本，编译打包的流程，当前代码的版本号。


> 最后，除了使用Eclipse这样的IDE进行编译外，我们还必须能通过命令行工具进行编译，才能够让项目在一个独立的服务器上编译、测试、部署。


> 这些工作难度不大，但是非常琐碎且耗时。如果每一个项目都自己搞一套配置，肯定会一团糟。我们需要的是一个标准化的Java项目管理和构建工具。



## Maven安装

1. 前提```cmd
c:\> java -version
```


2. 下载 maven
[Maven – Download Apache Maven](http://maven.apache.org/download.cgi)
3. 解压后配置环境变量
![](Pasted%20image%2020210803170154.png#alt=)
4. 安装完成```
c:\> mvn -v
```




## Maven 项目结构

一个使用Maven管理的普通的Java项目，它的目录结构默认如下：

```ascii
a-maven-project
├── pom.xml
├── src
│   ├── main
│   │   ├── java
│   │   └── resources
│   └── test
│       ├── java
│       └── resources
└── target
```

模块化项目结构

```ascii
                        ┌ ─ ─ ─ ─ ─ ─ ┐
                          ┌─────────┐
                        │ │Module A │ │
                          └─────────┘
┌──────────────┐ split  │ ┌─────────┐ │
│Single Project│───────>  │Module B │
└──────────────┘        │ └─────────┘ │
                          ┌─────────┐
                        │ │Module C │ │
                          └─────────┘
                        └ ─ ─ ─ ─ ─ ─ ┘
```

```ascii
multiple-project
├── pom.xml
├── parent
│   └── pom.xml
├── module-a
│   ├── pom.xml
│   └── src
├── module-b
│   ├── pom.xml
│   └── src
└── module-c
    ├── pom.xml
    └── src
```

> 项目的根目录`a-maven-project`是项目名，它有一个项目描述文件`pom.xml`，存放Java源码的目录是`src/main/java`，存放资源文件的目录是`src/main/resources`，存放测试源码的目录是`src/test/java`，存放测试资源的目录是`src/test/resources`，最后，所有编译、打包生成的文件都放在`target`目录里。这些就是一个Maven项目的标准目录结构。



## Maven POM?

描述了项目、依赖等。

```
<project ...>
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.itranswarp.learnjava</groupId>
	<artifactId>hello</artifactId>
	<version>1.0</version>
	<packaging>jar</packaging>
	<properties>
        ...
	</properties>
	<dependencies>
        <dependency>
            <groupId>commons-logging</groupId>
            <artifactId>commons-logging</artifactId>
            <version>1.2</version>
        </dependency>
	</dependencies>
</project>
```


### groupId、artifactId、version

作为Java工程或第三方库(依赖)的唯一标识。

> 其中，`groupId`类似于Java的包名，通常是公司或组织名称，`artifactId`类似于Java的类名，通常是项目名称，再加上`version`，一个Maven工程就是由`groupId`，`artifactId`和`version`作为唯一标识。我们在引用其他第三方库的时候，也是通过这3个变量确定。


可在[Maven Central Repository Search](https://search.maven.org/)查找第三方组件的groupId、artifactId、version


## classpath?

> `classpath`是JVM用到的一个环境变量，它用来指示JVM如何搜索`class`。



## Maven镜像

Maven 有自己的中央仓库（[repo1.maven.org](https://repo1.maven.org/)），第三方库将自身的jar以及相关信息上传至中央仓库，Maven就可以从中央仓库把所需依赖下载到本地。


### .m2目录

Maven缓存目录


### 更换仓库镜像

在用户主目录下进入`.m2`目录，创建一个`settings.xml`配置文件，内容如下：

```
<settings>
    <mirrors>
        <mirror>
            <id>aliyun</id>
            <name>aliyun</name>
            <mirrorOf>central</mirrorOf>
            <!-- 国内推荐阿里云的Maven镜像 -->
            <url>https://maven.aliyun.com/repository/central</url>
        </mirror>
    </mirrors>
</settings>
```


### IDEA导入新项目无法下载对应依赖的解决办法

找同事将他的依赖copy一下放置以下文件夹（此为依赖缓存目录）
![](Pasted%20image%2020210803182825.png#alt=)


## Maven 生命周期

- Clean Lifecycle 在进行真正的构建之前进行一些清理工作。
- Default Lifecycle 构建的核心部分，编译，测试，打包，部署等等。
- Site Lifecycle 生成项目报告，站点，发布站点。

> 使用Maven构建项目就是执行lifecycle，执行到指定的phase为止。每个phase会执行自己默认的一个或多个goal。goal是最小任务单元。
执行每个phase，都是通过某个插件（plugin）来执行的，Maven本身其实并不知道如何执行`compile`，它只是负责找到对应的`compiler`插件，然后执行默认的`compiler:compile`这个goal来完成编译。



## mvnw？

> `mvnw`是Maven Wrapper的缩写。因为我们安装Maven时，默认情况下，系统所有项目都会使用全局安装的这个Maven版本。但是，对于某些项目来说，它可能必须使用某个特定的Maven版本，这个时候，就可以使用Maven Wrapper，它可以负责给这个特定的项目安装指定版本的Maven，而其他项目不受影响。


> 简单地说，Maven Wrapper就是给一个项目提供一个独立的，指定版本的Maven给它使用。


> Maven Wrapper的另一个作用是把项目的`mvnw`、`mvnw.cmd`和`.mvn`提交到版本库中，可以使所有开发人员使用统一的Maven版本。



# 使用IDEA+Maven构建HelloWorld项目

![](Pasted%20image%2020210804111941.png#alt=)
![](Pasted%20image%2020210804113014.png#alt=)
![](Pasted%20image%2020210804113033.png#alt=)
![](Pasted%20image%2020210804113205.png#alt=)
![](Pasted%20image%2020210804113322.png#alt=)
![](Pasted%20image%2020210804113353.png#alt=)


## archetype

通过archetype创建相应的项目目录。可以想象成archetype中有很多项目模板，通过archetype可快速生成对应的项目目录结构。


# 


# 参考

1. [Maven介绍 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1252599548343744/1309301146648610)
2. [classpath和jar - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1252599548343744/1260466914339296)
3. [IDEA+MAVEN：踩坑指南 - 知乎](https://zhuanlan.zhihu.com/p/104311658)
4. [Maven生命周期详解 - imsoft - 博客园](https://www.cnblogs.com/imsoft/p/maven.html)
5. [Maven的声明周期(Lifecycle )和命令(Phase) - 码农神说 - 博客园](https://www.cnblogs.com/zhaiqianfeng/p/4620138.html)
6. [使用插件 - 廖雪峰的官方网站](https://www.liaoxuefeng.com/wiki/1252599548343744/1309301217951777)
