### Enterprise Java Beans (EJB)

- Enterprise Java Beans, or EJBs, are another API within Java EE that provide a standard component architecture for building object-oriented business applications. An EJB is a reusable Java object that runs in a special runtime environment known as an EJB container. In the past EJBs needed to be accompanied by XML, or they needed to adopt a certain signature. But they've been greatly simplified in the latest versions of Java EE and have adopted a POJO-based approach that uses annotations. EJBs typically handle the application logic that supports business operations for a system, so you will typically find centralized processing logic that interacts with the database. This centralizes the system's business logic so that it can be reused by multiple clients. Because EJBs are managed in a container EJBs can benefit from additional services, such as transactions, connection pooling, or multithreading without writing explicit code. When architecting a system with EJBs an interface is defined for the EJB and an implementation is built. The EJBs often handle core logic and concerns like data persistence. The EJB implementation runs inside of the EJB container and is injected into other Java EE components, such as JSF backing beans or servlets through a JNDI lookup of the EJB. Once the EJB is injected into these components they can leverage the business services contained within EJB and benefit from the container-provided services. This pulls core business logic out of components running in the web tier so they can be centralized and reused.

- The EJB implementation runs inside of the EJB container and is injected into other Java EE components, such as JSF backing beans or servlets through a JNDI lookup of the EJB.

- EJB 3.0+ supports Annotations

- What is an EJB?

  - Java class or POJO (Plain Old Java Object)?
  - Isolates system business logic
  - Managed by an EJB container
  - Benefit from container-provided services

- EJB Benefits - It provides features such as:

  - Transactions
  - Security
  - Concurency
  - Networking
  - Persistance

- EJB Types
  - Session Beans - Contains business logic that models an action or use case.
    - Stateful Session Beans - `@Stateful` - Unique for every client
    - Stateless Session Beans - `@Stateless` - Shared for every client
    - Singelton Session Beans - `@Singelton` - Shared for every client and maintain state at App. level
  - Message Driven Bean - Bean that processes messages sent by other components.

#### CDI (Contexts and dependency injection)

- CDI or contexts and dependency injection was introduced in Java EE 6. The introduction of CDI provided Java developers with an alternative approach known as dependency injection for structuring their applications. There are two main concepts at the center of CDI, beans and dependency injection. Through Java's history there was always the concept of a bean. However, until Java EE 6 it wasn't clearly agreed upon. Java EE 6 introduced the managed bean standard which defines beans as non-static POJOs that contain business logic which are managed by a container. Managed beans can then be injected into other Java EE components, such as servlets, JAX-RS resources, and other beans. It's important to remember, that an object must be a bean to be used for dependency injection, which is the other core concept in CDI. Dependency injection changes how objects are created. Instead of creating objects using the new operator and constructor, the container instantiates objects as beans. Beans with dependencies on other objects rely upon the container to inject those objects instead of instantiating them themselves. So for example, the Bean A object has a dependency on Bean B. Using dependency injection the container injects Bean B into Bean A. We can indicate that a bean should be injected into a servlet or other bean using the Inject annotation. Where we place the Inject annotation is known as the injection point. When determining which bean to inject, the container considers the type of dependency and selects a bean of matching type for injection. Understanding these concepts will help you be successful with CDI. Within Java EE CDI's main features include dependency injection which is based upon the bean type. It also features contexts that define the scope of a bean within the CDI container. These features allow developers to create application code that is loosely coupled making the application more flexible and robust. Additionally CDI managed beans benefit from services provided by the container such as autodiscovery, qualifiers, scopes, and naming that can be leveraged by expression language. Within CDI there are two types of bean archives that use different discovery modes. The first type of bean archive is known as explicit because it explicitly defines the discovery mode in a beans.xml file located within the project. With discovery mode all every object is created as a bean within the archive. Implicit archives are the default. They do not contain a beans.xml file and they set the discovery mode to annotate it which causes only those beans with a bean defining annotation to be instantiated within the container. Bean-defining annotations include the scope annotations that we'll discuss next. Every bean has a scope which determines the life cycle of its instances and their visibility to other beans. The default scope is Dependent which causes a bean to assume the scope of the bean it's injected into. Request and Session scopes are used to tie the scope of a bean to either an HTTP request or an HTTP session. ApplicationScoped beans have a larger scope that causes a single instance of the bean to be shared across the entire application. Finally, the ConversationScoped bean is particular to JSF, and it's explicitly controlled by the developer through their application code. Now, sometimes we have ambiguity between our beans, they may share the same type. So within CDI you will find support for qualifiers which can instruct the container to inject a particular bean when multiple beans in the container have a similar type. This is necessary for resolving that ambiguity when we're injecting our beans because the default mechanism is type based. Additionally CDI allows us to build custom qualifiers which are type safe and they allow for more granular control of dependency injection within CDI. So that's an overview of CDI.

- What is a Bean?

  - Non-static POJO's, concrete class containing business logic
  - Instantiated, managed, and injected by a container
  - Managed bean can be injected into Servlet, JAX-RS resources, message-driven beans, other managed beans

- What is Java CDI?
  - Provides a standard dependency injection framework
  - Bind Beans to lifecycle contexts
  - Imporoves the structure of application code (less coupling)
  - Managed beans benefit from container-provided services (auto discovery, qualifiers, scopes, and namings)
- Discovery Mode - Within CDI there are two types of bean archives that use different discovery modes

  - Explicit
    - Contains a beans.xml with bean-discovery-mode = `all`
    - CDI version 1.1 or greater
  - Implicit (Default)
    - Contains one or more classes with a bean-defining annotaion
    - No beans.xml, default bean-discovery-mode = `annonated`

- Scopes - scope determines the life cycle of the Bean

  - `@Dependent` - Default - the same scope as its client bean
  - `@RequestScoped` - A single HTTP Request
  - `@SessionScoped` - Spans multiple http requests
  - `@ApplicationScoped` - Shared accross the entire application
  - `@ConversationScoped` - Explicitly controlled boundaries withing a JSF application

- Qualifiers - Requires to resolve ambiguity, when multiple beans share the same type/scope

  - Used to resolve ambiguity among beans of the same type
  - Indicates a particular bean instance should be injected
  - Allows for custom qualifiers

- Interceptor Methods
  - To introduce cross cutting concerns within the BEAN/Application
