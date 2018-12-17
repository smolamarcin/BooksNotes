### What is spring framework? Why Java programmer should use Spring framework?

Spring is a framework which helps Java programmer in development. Spring provides Dependency Injection and IOC container, Spring MVC flow and several useful API for Java programmer.



### Is Spring controller/service/singleton thread-safe?

It depends. The main factor is the scope of a bean.

### Scopes of a beans

* Singleton - Scopes a single bean definition to a single object instance per Spring IoC container.

* Prototype -  Scopes a single bean definition to any number of object instances.

* Request - copes a single bean definition to the lifecycle of a single HTTP request; that is each and every HTTP request will have its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring ApplicationContext.

* Session - Scopes a single bean definition to the lifecycle of a HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext.

* Global Session - Scopes a single bean definition to the lifecycle of a global HTTP Session. Typically only valid when used in a portlet context. Only valid in the context of a web-aware Spring ApplicationContext.

