## 历史，动机(motivation)

Argo起源与[58同城]的内部web框架wf(web framework)。

目前wf支撑着[58同城]几乎所有的web站点，包括wap和手机端的访问等，现在wf每天处理10亿级的请求。经过长时间的运作与运行，证明wf是一个可靠的、高效的web框架。


作为一个有一定规模的互联网企业，如果在变化的互联网环境中上线一个项目，在软件开发中需要在三方面进行平衡：

1. 运维，希望每个站点的配置和可执行部分分离，部署的方式相同；
1. 项目内部，希望程序员聚焦在业务上，可以快速实现产品需求、响应产品变化。
在此基础上，我们开发了wf。

Argo在wf做了大量优化和重构，以适应各组织软件开发的个性化需求，提升了系统性能，具有更好的可扩展性。Argo的开源反过来也促进wf2.0的开发。


## 哲学观 (philosophy)
1. [约定优于配置]，减少软件开发人员需做决定的数量，获得简单的好处，而又不失灵活性。Argo体系中有且只有一个组织级约定，规定包的命名，配置文件路径，日志文件路径等。组织的约定是不容侵犯，每个项目在组织级约定下工作。组织级约定建议以jar形式下发给各项目。
1. 简单，Argo可以不需要任何配置文件，项目代码结构简单，易于维护。
1. 纪律，包和类的命名都受组织级约定的控制，任何违反约定的行为可能导致系统无法正常运行。

## 系统特点 (features)

1. SEO友好的URL结构，Argo天然支持RESTful的url结构，并能自动匹配合适的参数；
1. 零配置，甚至你不要web.xml就能在tomcat上运行；
1. 插拔式组件架构，可以灵活扩张功能；
1. 高安全性，提供集群模式下，避免ip欺骗等功能。

## 系统约定 (convention)

Argo不是一个通用的web框架，一个问题解决方案可能有很多，但在Argo中只提供一种解决方案。Argo在以下约定中工作：

1. servlet 3.0环境，主要针对Tomcat 7.x；
1. 基于[guice]的Ioc，组织和项目可以各提供一个module注入模块，而且module的命名必须符合约定；
1. maven依赖，项目的代码体系和maven默认代码体系一致，maven以插件提供开发过程中所需要的开发运行环境（[jetty:run]或[tomcat7:run]）。

## Hello World

请参考例子 samples/hello-world

```shell
mvn tomcat7:run
```

或者
```shell
mvn jetty:run
```

然后浏览

http://localhost/

## 进阶

TODO

## 如何实现 (how)

TODO

## 更新日志
### 2013-03-21
1. 修正 issues #1, #2,
1. 修正 ContextPath不是根目录("/")下无法正常运行的bug
1. 提供model中默认参数 __beat,便于在view中使用
1. 提供war:war打包plugin实例，移除web.xml的依赖

```xml

<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-war-plugin</artifactId>
  <version>2.3</version>
  <configuration>
    <failOnMissingWebXml>false</failOnMissingWebXml>
  </configuration>
</plugin>

```

[58同城]: http://www.58.com/
[约定优于配置]: http://zh.wikipedia.org/wiki/%E7%BA%A6%E5%AE%9A%E4%BC%98%E4%BA%8E%E9%85%8D%E7%BD%AE
[guice]: http://code.google.com/p/google-guice/
[jetty:run]: http://docs.codehaus.org/display/JETTY/Maven+Jetty+Plugin
[tomcat7:run]: http://tomcat.apache.org/maven-plugin-2.0/tomcat7-maven-plugin/run-mojo.html

