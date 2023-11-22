```java
SecurityConfig.java
@Configuration
public class SecurityConfig extends WebSecurityConfigurerAdapter
{
    @Override
    protected void configure(HttpSecurity http) throws Exception
    {
        http
         .csrf().disable()
         .authorizeRequests().anyRequest().authenticated()
         .and()
         .httpBasic();
    }

    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth)
            throws Exception
    {
        auth.inMemoryAuthentication()
        	.withUser("admin")
        	.password("{noop}password")
        	.roles("USER");
    }
}
```

有上面这么一段就实现了BasicAuth。

## 什么是 WebSecurityConfigurerAdapter

## 什么是 void config()

意思就是：我要配置HttpSecurity 、AuthenticationManagerBuilder …

* void config(HttpSecurity http)

可以在这里配置哪些路径需要验证、采用什么认证等等。

* void configGlobal(AuthenticationManagerBuilder auth)

身份认证管理生成器，在这里与数据库交互，验证用户名密码。



## 参考

1. [Securing Spring Boot REST API with Basic Auth - HowToDoInJava](https://howtodoinjava.com/spring-boot2/security-rest-basic-auth-example/)
2. [Spring Security Java Config Preview: Web Security](https://spring.io/blog/2013/07/03/spring-security-java-config-preview-web-security/)