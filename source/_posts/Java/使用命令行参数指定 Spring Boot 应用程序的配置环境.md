---

title: 使用命令行参数指定 Spring Boot 应用程序的配置环境
date: 2022-12-07 20:44
tags: [Java,Spring Boot]

---

## 〇、问题
最近接触实际的Java项目，看到其中使用下列方式就可以指定在程序运行时使用哪个配置文件，对此不甚了解，在此学习并记录一下如何使用命令行参数来指定Spring Boot应用程序的配置环境。
```bash
java -jar demo.jar --spring.profiles.active=test
```
<!-- more -->
## 一、配置文件约定
### 1.1 格式：
```
application-{profile}.yml
```
一个项目一般会有开发、测试、正式三个环境，在配置文件命名上就可以采用下列方式：
```
application.yml      
application-dev.yml
application-test.yml
application-prod.yml
```

### 1.2 加载顺序
先加载`application.yml`，然后根据`application.yml`中的配置信息继续加载后续文件，例如，配置文件内容如下：

```yml 
#application.yml
spring:
	profiles:
		active: test
```

```yml 
#application-dev.yml
spring: 
	application: 
		name: dev
```

```yml 
#application-test.yml
spring: 
	application: 
		name: test
```

```yml 
#application-prod.yml
spring: 
	application: 
		name: prod
```
首先加载`application.yml`，其中指定了需要激活命为`test`的配置文件，即，将会去加载`application-prod.yml`。
另外可以指定多个配置文件，如：
```yml 
#application.yml
spring:
	profiles:
		active: prod,live
```
将会先后加载`prod`与`live`两个配置文件，如果其中有相同的配置项，后激活的配置文件中的配置项将会覆盖先激活的配置项。

### 1.3 路径
`src/main/resources`

## 二、通过命令行指定配置文件
```bash
java -jar demo.jar --spring.profiles.active=test
```
如果不通过`--spring.profiles.active=test`指定配置文件，则`application.yml`中配置哪个就激活哪个。

## 三、如何不重新打包指定修改配置文件
有时在项目打包上线后可能会发生需要修改某个配置项的情况，此时可以通过在jar包所在文件夹内创建`config`文件夹，并将新的配置文件拷贝到`config`下达到覆盖打包时的配置文件的目的，文件夹结构如下：
```
- deme.jar
- config
  |- application.yml
  |- application-dev.yml
  |- application-prod.yml

```

## 参考
1. [Core Features](https://docs.spring.io/spring-boot/docs/current/reference/html/features.html#features.external-config.files.profile-specific)