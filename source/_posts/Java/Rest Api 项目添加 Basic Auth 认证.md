---

title: Rest Api 项目添加 Basic Auth 认证
date: 2022-10-10 22:09
tags: [Java,Spring Boot,Rest Api,Basic Auth]

---
## 一、前言
一直浅显的认为Basic Auth是一种过时的，不安全的认证方式。但是最近接触IBPM的Rest Api，就是使用的Basic Auth认证。在此学习一下如何在通过Spring Security在Rest Api项目中使用Basic Auth认证。

<!-- more -->

## 二、步骤
### 2.1 添加spring-boot-starter-security依赖

```xml
// pom.xml
<dependency> <groupId>org.springframework.boot</groupId> <artifactId>spring-boot-starter-security</artifactId> </dependency>
```
### 2.2 配置Spring Security
创建一个继承了_**WebSecurityConfigurerAdapter**_的类：
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210102250634.png)
```java
@Configuration  
public class SecurityConfig extends WebSecurityConfigurerAdapter {  
    @Override  
    protected void configure(HttpSecurity http) throws Exception{  
        http  
                .csrf().disable()  
                .authorizeRequests()  
                .anyRequest().authenticated()  
                .and()  
                .httpBasic();  
    }  
  
    @Autowired  
    public void configGlobal(AuthenticationManagerBuilder auth) throws Exception{  
        auth  
                .inMemoryAuthentication()  
                .withUser("admin")  
                .password("{noop}password")  
                .roles("USER");  
    }  
}
```
### 2.3 Postman调用

![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210102253507.png)
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210102256033.png)

## 参考
1. [Securing Spring Boot REST API with Basic Auth - HowToDoInJava](https://howtodoinjava.com/spring-boot2/security-rest-basic-auth-example/)