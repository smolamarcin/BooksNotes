### What is spring framework? Why Java programmer should use Spring framework?

Spring is a framework which helps Java programmer in development. Spring provides Dependency Injection and IOC container, Spring MVC flow and several useful API for Java programmer.

### Component types: @Repository, @Controller, @Service, @Component -> What are differences?

With this annotations, Spring will automatically import the beans into the container and onject to dependencies.
@Autowiring handles only wiring part. Still, we need to declare our components, which are candidates to wire.

@Component
> Spring will automatically pick up this class, and pull it up into the applicaiton context. Also, unchecked exceptions thrown by dao methhods are aligible for transaction into Spring DAO exceptions.

@Repository
> This annotation provides additional benefits,e specially for DAO classes. It import class into the DI container. 

@Service
> At this moment there is no additional behaviour for this annotation, but it specifies our intent better. In future some tools can rely on this.

@Controller
> Mark class as Spring MVC controller. Also, inject bean into container.  When we place @Controller at the class level, we can mark methods with @RequestMapping to map URLs.

### Is Spring controller/service/singleton thread-safe?

It depends. The main factor is the scope of a bean.

### Scopes of a beans

* Singleton - Scopes a single bean definition to a single object instance per Spring IoC container.

* Prototype -  Scopes a single bean definition to any number of object instances.

* Request - copes a single bean definition to the lifecycle of a single HTTP request; that is each and every HTTP request will have its own instance of a bean created off the back of a single bean definition. Only valid in the context of a web-aware Spring ApplicationContext.

* Session - Scopes a single bean definition to the lifecycle of a HTTP Session. Only valid in the context of a web-aware Spring ApplicationContext.

* Global Session - Scopes a single bean definition to the lifecycle of a global HTTP Session. Typically only valid when used in a portlet context. Only valid in the context of a web-aware Spring ApplicationContext.

