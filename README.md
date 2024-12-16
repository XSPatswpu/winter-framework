# winter-framework
mini framework of spring framework

winter framework 是一个简化版的 spring 框架，只包括以下核心功能：
* IOC
* AOP
* JDBC & 事务
* Web MVC

项目意义：
1. 加深对 spring 框架的理解
2. 学习如何进行框架设计
3. 理解项目演进流程

## IOC
winter framework 暂时只支持核心的 IOC 容器功能，详细功能如下：
1. 使用 ApplicationContext 表示 IOC 容器
2. 配置方式只支持 Annotation
3. 支持按包名扫描
4. Bean 类型，只支持 Singleton
5. Bean 工厂，只支持 @Bean 注解
6. 依赖注入，支持构造方法、Setter方法与字段

## AOP

## JDBC & 事务

## Web MVC
