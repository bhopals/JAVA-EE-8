### WebSockets API

The WebSocket API is used to allow Java applications to communicate over the WebSocket protocol.

Highly interactive web applications have increased the need for two-way communication between browsers and servers. These apps need data to be pushed from the server at will without the client initiating a request. The HTTP standard protocol for Internet communications is inefficient at filling this requirement and developers started building polling mechanisms that continuously ping the server from the browser to potentially retrieve data. Sometimes there was data, sometimes there wasn't. These mechanisms are inefficient, because many connections are created and HTTP headers were required to be sent with every request. The WebSockets Protocol was developed to address these needs, allowing bidirectional, full duplex communication between the browser and server over TCP. Under the WebSockets protocol, a client initiates the connection via HTTP, and then the connection is upgraded to the WebSockets protocol. Once connected, the server or client can send messages at any time without the client initiating the communication. This significantly reduces the number of connections required. The WebSockets protocol provides a better way to architect highly interactive web application, and support for the protocol is provided by Java EE's WebSockets API. Within the API, there are two approaches for working with WebSockets. The simplest approach is the annotation-based approach where annotations supporting WebSockets are added to POJOs. The programmatic approach requires developers to implement certain API interfaces for working with WebSockets. These interfaces handle connections, message sending, and consumption. Additionally, this approach requires some configuration classes to be created. It's a little bit more heavy weight than the annotation-based approach. We'll primarily be working with annotations throughout this chapter, and we'll use them to create WebSockets very easily and in a simplistic manner. In WebSockets, the connection is established between two peers who exchange messages bidirectionally. The Java EE API refers to the peer initiating the connection as the ClientEndpoint. An endpoint simply represents one side of the connection. The ServerEndpoint accepts the connection and then the two peers exchange messages over a session until one peer ends the connection. It's also important to understand that multiple peers may be connected to the ServerEndpoint. This allows the ServerEndpoint to broadcast messages to a group of peers simultaneously. When working with the Java WebSockets API, it is likely that you will be primarily working with ServerEndpoint, because the primary client is typically a web browser. Let's take a quick look at the annotations used to build WebSockets endpoints. The ServerEndpoint annotation is placed at the class level to create an endpoint. When the application is deployed, this class is then made available at the path specified in the annotation. The next four annotations that begin with on provide hooks into the different events in the endpoint's life cycle. They are annotated to a method to be invoked when a particular event occurs, sort of like a listener. These annotations provide hooks for when a Socket session is opened, we receive a message, or an error occurs, or the session is closed.

- ClientEndpoint
- ServerEndpoint
- Connection
- Session

- Endpoint Annotations

  - `@ServerEndpoint('/path')` - Declares the annotated class as a WebSocket endpoint at the specified path.
    - Class Level Annotation
  - `@OnOpen` - Invokes the annotated method when a WebSocket session is opened
  - `@OnMessage` - Invokes the annotated method when a message is received by a peer
  - `@OnError` - Invokes the annotated method when errors occur
  - `@OnClose` - Invokes the annotated method when the session is closed

- TOOL
  - Socket Wranch
