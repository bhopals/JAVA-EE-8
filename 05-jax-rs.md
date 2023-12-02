### JAX-RS

#### REST OVERVIEW

In REST architecture, API clients send requests to an API and receive responses over HTTP. The HTTP request contains information such as the URI and the request method that informs the API of a desired operation or data the client is requesting. The API maps request information to an endpoint and then returns a response to the client in adjacent format over HTTP. The response contains resource representations for requested data or information about the operation performed as the result of the client request. The client then receives the response from the API and processes the information returned by the API. Let's look at a quick example to learn more. This REST API provides endpoints that correspond the operations to an inventoryitems resource. It exposes five endpoints for the resource that generally map to CRUD operations. To the left of the endpoints, you see the request methods or operations and their corresponding mappings to CRUD operations. Some operations like post require API clients to provide additional information in the HTTP request body, such as the inventory item to create. This is typically provided in adjacent format. Other endpoints may require information to be supplied in the URL, which is denoted by the template parameters in curly braces. As we progress in this chapter, we'll see how JAX-RS can be used to easily construct REST API implementations in Java EE that conform to these standards.

#### JAX-RS

- Java API for RESTful web services

The Java API for RESTful web services or JAX-RS provides an API for development of web services built using the REST architectural style. Java EE developers can use JAX-RS to simplify the development of REST-based services using an approach centered around POJOs, annotations and the HTTP protocol. The JAX-RS API allows developers to built simple POJOs that are annotated to support the construction of a REST API. The annotations are primarily applied to classes known as resources and their methods known as resource methods. These classes provide an implementation for REST API resources and endpoints found in the design of an API. JAX-RS annotations map to parts of the HTTP request providing developers easy access to data sent in the request. This eliminates the need to parse an HTTP request. Most JAX-RS implementations are built on top of the servlet API. However, they abstract away lower level requests and response processing code necessary for working with servlets. Let's get a quick overview of how it works. The annotation-based approach in JAX-RS makes it easy to establish a JAX-RS application. Using the ApplicationPath annotation, we establish the base URI for endpoints or resource paths in the API. In this example, the HsportsRestApplication class is annotated with the ApplicationPath annotation and extends the Application class. This sets up the base path for the API as /hsports/api. JAX-RS REST APIs contain resources that correspond to objects within our domain that are exposed through API endpoints. To build a resource, we add the path annotation at the class level on a Java POJO to create an endpoint for accessing that resource. The path annotation is actually concatenated then with the base URI that we specified using the ApplicationPath annotation. Within the resource class, we create resource methods to handle the incoming HTTP calls to the API. When JAX-RS selects the appropriate resource method to handle an HTTP request, it uses these mapping annotations to determine which method to invoke. The GET annotation on our getItem resource method impacts this selection. It indicates that the getItem method will only handle HTTP GET requests so if we received an HTTP POST, this method would not be invoked. The Produces and Consumes annotations also impact how a resource method is selected. There is matching that occurs when we receive the request based upon the media types provided or consumed by a resource method. These map to the Accepts and Content-Type headers on the request. When building resources, we can apply the Path annotation at the resource method level to construct new endpoints within the resource class. Additionally, the Produces and Consumes annotations can be applied at the resource level for more granular control of our request mappings. The JAX-RS API contains additional annotations that allow us to map almost every part of the request, including path parameters, query parameters, cookies and headers from the HTTP request. You will see several of these in action in the upcoming lessons. Another great feature of JAX-RS is its support for custom serialization to the designated media type for custom objects. This example returns a custom POJO from the resource method which JAX-RS serializes to our defined media type JSON. So JAX-RS is able to handle the conversion from a Java object to a response format such as JSON without any code by the developer. On the contrary, JAX-RS supports deserialization of JSON to custom object types. This example deserializes the JSON in the request body to a custom item type specified as a parameter in the resource method. These features make JAX-RS a great option for Java EE developers that architect their applications using REST APIs.

- JAX-RS

  - POJO-based approach to development of REST APIs
  - Annotation-based creation of REST Resources
  - HTTP Centric
  - Commonly implemented on top of Servlets

- `@ApplicationPath("/v1/api")` - Base URI for ENDPOINTS or RESOURCE PATH for the API - The class should extend `Application` class
- JAX-RS REST APIs contain resources that correspond to objects within our domain that
  are exposed through API endpoints. To build resources, we add `@Path` annotation at the class level on
  a Java POJO (`@Path`, `@Produces("application/json")`, `@Consumes("application/json")`) to creat an endpoint
  for accessing that resource.

- Mapping Annotations

  - `ApplicationPath`
  - `@Path`
  - `@Produces` - Serialization (Java Object to RESPONSE TYPE object)
  - `@Consumes`
  - `@GET`, `@POST`, `@PUT`, `@DELETE`
  - `@PathParam` - Extracts a value from the URI of the HTTP Request
  - `@QueryParam` - Extracts a parameter from the HTTP Request
  - `@CookieParam` - Extracts a cookie from the HTTP Request
  - `@HeaderParam` - Extracts a header from the HTTP Request
  - `@FormParam` - Extracts a form parameter from the HTTP Request
  - `@MatrixParam` - Extracts a matrix parameter from the HTTP Request

- Asynchronous Feature

  - Create a method
  - Pass second params -AsyncReponse - `@Suspended AsyncReponse ar`
  - Create Thread instance - `new Thread() { public void run() {...}}.start()`
  - use `Future` - Future<InventoryService>

- Reactive Feature

  - JAX-RS client receives support for the Reactive programming style which provides developers with a more succinct way of handling asynchronous calls. Under the Reactive approach, we avoid the use of callbacks instead opting to use a completion stage that allows a chain of stages to be completed asynchronously. Let's take a look at using the Reactive
  - Use `CompletionStage` - java.util.concurrent.CompletionStage

- Server-Sent Events
  - Server sent events allow us to establish a one-way channel from a server to a client which can be reused to send multiple events.
  - `SseEventSink`, `OutboundSseEvent`
