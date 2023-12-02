### Java Message Service (JMS)

The Java Messaging Service, or JMS, has been a part of Java EE since version 1.2, so it's been a part of the platform for a while. The introduction of JMS version 2.0 simplified the JMS API, making it much easier to work with the messaging technology. Messaging is a common integration pattern used by Java applications, and there are many middle-tier messaging service implementations. The JMS API provides a common approach and schemantics for Java applications that use messaging. It also defines roles for messaging services, known as JMS providers. The messaging concepts in JMS can be applied by developers to use multiple JMS providers without specific knowledge of each of them. Within JMS we'll find support for two styles of messaging, point-to-point and publish subscribe. Let's dive into the details of these two styles. If we look at the point-to-point messaging style, you will see that it starts with the JMS producer writing a message to a queue. The message is then consumed off the queue by a single JMS consumer, so one producer sends a message to one consumer. The publish/subscribe messaging style uses a topic instead of a queue. The topic allows messages to be distributed to multiple JMS consumers instead of a single consumer. The structure of a JMS message contains three sections. The headers, properties, and body. The JMS headers are fixed across all JMS messages. These headers include the destination, delivery method, message ID, delivery time, and other envelope information. The properties section of the message allows producers or the JMS provider to add optional headers to the message that can be read by consumers. The body of a JMS message can be one of five types, providing support for streams, maps, text, objects, and bytes. Next, let's take a look at the JMS APIs that are used to send and receive messages. Within the JMS API, we primarily use four interfaces for sending and receiving messages. The ConnectionFactory can be used by a JMS client to obtain a connection with the JMS provider. It also contains all of the configuration information regarding the connection. The JMSContext combines a connection and a session which are used to create the producer and the consumer. Typically the JMSContext is container managed within a Java EE application. The consumer API is the interface used to read messages from a topic or a queue. Contrarily, the producer is used for sending messages.

- Java messaging API (Not the actual message system)
  - There are many middle tier implementations
- Supports message creation, delivery, receipt, and reading
- Guarantees delivery between systems
- It also defines roles for messaging services, know as JMS Providers.
- Supports `point-to-point` and `publish-subscribe` models

- JMS Producer
- JMS Consumer
- JMS Provider
  - Point-To-Point - QUEUE
  - Publish/Subscribe - TOPIC
- Java EE Application Server
- Message

- JMS API's to SEND and RECEIVE Messages (4 Interfaces)

  - ConnectionFactory - Encapsulates the connection configuration parameters
  - JMS Context
    - Provides a combination of the session and connection
    - Allows for the creation of consumers and producers
  - JMSConsumer - Object for reading messages to a QUEUE or TOPIC
  - JMSProducer - Object for building and sending messages to a QUEUE or TOPIC

- EXAMPLE

  - Create Queue in Wildfly server
  - Go to `bin` directory
  - run command
    `/subsystem=messaging-activemq/server=default/jms-queue=HsportsQueue:add(entries=[java:/jms/queue/HsportsQueue])`

- ActiveMQ - Open Source Message Queue
