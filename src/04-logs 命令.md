
- 语法

> `docker logs [OPTIONS] CONTAINER`
>
> - OPTIONS说明：
>
>   `-f`：跟踪日志输出
>
>   `--since`：显示某个开始时间的所有日志
>
>   `-t`：显示时间戳
>
>   `--tail`：仅列出最新N条容器日志

- 实例

> 跟踪查看容器 `hzero-iam` 的日志输出
>
> `docker logs -f hzero-iam`

```
[root@localhost ~]# docker logs -f hzero-iam
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/hzero-iam.jar!/BOOT-INF/lib/logback-classic-1.2.3.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/hzero-iam.jar!/BOOT-INF/lib/log4j-slf4j-impl-2.10.0.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [ch.qos.logback.classic.util.ContextSelectorStaticBinder]
2021-09-08 13:37:02.944  INFO 1 --- [           main] s.c.a.AnnotationConfigApplicationContext : Refreshing org.springframework.context.annotation.AnnotationConfigApplicationContext@1b344b0a: startup date [Wed Sep 08 13:37:02 CST 2021]; root of context hierarchy
2021-09-08 13:37:05.606  INFO 1 --- [           main] f.a.AutowiredAnnotationBeanPostProcessor : JSR-330 'javax.inject.Inject' annotation found and supported for autowiring
2021-09-08 13:37:06.366  INFO 1 --- [           main] trationDelegate$BeanPostProcessorChecker : Bean 'configurationPropertiesRebinderAutoConfiguration' of type [org.springframework.cloud.autoconfigure.ConfigurationPropertiesRebinderAutoConfiguration$$EnhancerBySpringCGLIB$$885d25a0] is not eligible for getting processed by all BeanPostProcessors (for example: not eligible for auto-proxying)

██╗  ██╗███████╗███████╗██████╗  ██████╗ 
██║  ██║╚══███╔╝██╔════╝██╔══██╗██╔═══██╗
███████║  ███╔╝ █████╗  ██████╔╝██║   ██║
██╔══██║ ███╔╝  ██╔══╝  ██╔══██╗██║   ██║
██║  ██║███████╗███████╗██║  ██║╚██████╔╝
╚═╝  ╚═╝╚══════╝╚══════╝╚═╝  ╚═╝ ╚═════╝ 
:: hzero-iam ::          (v1.6.3.RELEASE.RELEASE)
                                
2021-09-08 13:37:16.690  INFO 1 --- [           main] org.hzero.iam.IamApplication             : The following profiles are active: dev
2021-09-08 13:37:17.148  INFO 1 --- [           main] ConfigServletWebServerApplicationContext : Refreshing org.springframework.boot.web.servlet.context.AnnotationConfigServletWebServerApplicationContext@a11b0de: startup date [Wed Sep 08 13:37:17 CST 2021]; parent: org.springframework.context.annotation.AnnotationConfigApplicationContext@1b344b0a
2021-09-08 13:38:00.337  INFO 1 --- [           main] o.s.b.f.s.DefaultListableBeanFactory     : Overriding alias 'hzero-oauthFeignClient' definition for registered name 'org.hzero.iam.infra.feign.UserDetailsClient' with new target name 'org.hzero.iam.infra.feign.ClientDetailsClient'
2021-09-08 13:38:00.424  INFO 1 --- [           main] o.s.b.f.s.DefaultListableBeanFactory     : Overriding alias 'hzero-oauthFeignClient' definition for registered name 'org.hzero.iam.infra.feign.ClientDetailsClient' with new target name 'org.hzero.iam.infra.feign.OauthAdminFeignClient'
2021-09-08 13:38:03.954  INFO 1 --- [           main] o.s.b.f.s.DefaultListableBeanFactory     : Overriding alias 'hzero-platformFeignClient' definition for registered name 'org.hzero.iam.infra.feign.PermissionRuleFeignClient' with new target name 'io.choerodon.mybatis.helper.feign.LanguageRemoteService'
2021-09-08 13:38:05.347  INFO 1 --- [           main] o.s.b.f.s.DefaultListableBeanFactory     : Overriding alias 'hzero-interfaceFeignClient' definition for registered name 'org.hzero.boot.interfaces.infra.feign.InterfaceFeignClient' with new target name 'org.hzero.boot.interfaces.monitor.feign.HitfRemoteService'
```

> 查看容器 `hzero-iam` 从 2021年09月08日 后的最新 10 条日志
>
> `docker logs --since="2016-09-08" --tail=10 hzero-iam`

```
[root@localhost ~]# docker logs --since="2016-09-08" --tail=10 hzero-iam
2021-09-08 16:04:39.162  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Getting all instance registry info from the eureka server
2021-09-08 16:04:39.169  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : The response status is 200
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Disable delta property : true
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Single vip registry refresh property : null
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Force full registry fetch : false
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Application is null : false
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Registered Applications size is zero : false
2021-09-08 16:04:49.170  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Application version is -1: false
2021-09-08 16:04:49.171  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : Getting all instance registry info from the eureka server
2021-09-08 16:04:49.179  INFO 1 --- [freshExecutor-0] com.netflix.discovery.DiscoveryClient    : The response status is 200
```


- 参考文献
---
`[ 1 ]` [`Docker 教程`](https://www.runoob.com/docker/docker-tutorial.html)
