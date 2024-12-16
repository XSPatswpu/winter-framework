# 需求梳理
winter framework IOC 容器功能：
1. 自动创建被 "注解" 标记的 Bean 对象
2. 自动处理各个 Bean 之前的依赖关系
3. 提供用户接口，支持从容器中获取 Bean 对象

# 模块设计
## ApplicationContext
ApplicationContext 设计为用户侧接口，接口功能如下：
1. 根据 beanName 获取 Bean 对象，如发现多个抛出 NotSuchBeanDefinitionException
2. 根据 beanName 和 Class 指定获取单个 Bean 对象，如发现多个抛出 NotSuchBeanDefinitionException
3. 根据 Class 类型获取唯一 Bean 对象，抛出 NotSuchBeanDefinitionException
4. 根据 Class 类型获取 Bean 对象列表

## ConfigurationApplicationContext
ConfigurationApplicationContext 继承 ApplicationContext 提供框架层面需要使用的接口。提供获取 BeanDefinition 能力，接口功能如下：
1. 根据 beanName 获取 BeanDefinition，抛出 NotSuchBeanDefinitionException
2. 根据 beanName 和 Class 获取唯一 BeanDefinition，抛出 NotSuchBeanDefinitionException
3. 根据 Class 获取唯一 BeanDefinition，抛出 NotSuchBeanDefinitionException
4. 根据 Class 获取 BeanDefinition 列表

## AnnotationConfigApplicationContext
AnnotationConfigApplicationContext 使用注解方式实现 IOC 容器，主要功能如下：
1. .class 文件扫描获取包名，根据包名创建 BeanDefinition
2. @Bean @Configuration 注解扫描
3. 处理 Bean 依赖注入
4. beanPostProcessor 支持

# 详细设计

# Q & A
1. SpringApplication.run(UserApplication.class, args) 方法阻塞的原因？
可能是 Web Server 需要监听端口导致阻塞。