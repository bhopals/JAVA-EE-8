### Java Persistence API (JPA)

The Java Persistence API, or JPA, is a Java EE API for accessing, persisting, and managing Java objects and a relational database. It is one of my favorite APIs because it makes it incredibly simple to perform CRUD operations against a relational data store. JPA supports object-relational mapping, which is a technique for using an annotated object model for persisting data to a relational database. This greatly simplifies how we read, write, update, and delete data in a database from our Java applications, which is also known as data persistence. Using object-relational mapping, it is possible to write Java applications that interact with a relational database without writing any SQL. When using JPA, developers only work with objects and the underlying SQL is handled by the JPA provider. It is important to note that JPA is just a specification or API. The underlying implementation is built by JPA providers. The most popular is hybernate, which is a JPA implementation provided by JBoss. JPA is typically broken down into four areas. the JPA API provides support for key objects such as the EntityManager, which is used to manage entities. We'll talk a little bit more about these concepts in a minute. The Java persistence query language, or JPQL, allows us to write a SQL-like query that is object-based. These queries work across database providers and are irrelevant to the underlying data store. The criteria API found in JPA provides a programmatic type-safe API for building queries against entities. It is very verbose to work with, but if you are looking for type-safety, it is the best option. Let's talk a little bit more about the concepts of an entity. An entity is an object that represents a table within your database schema. So if we have a customer table in the database, we'd normally create a customer class which would be the entity. Within the customer class, fields are created on the class that correspond with every column in the customer table. Annotations are then applied on the class and field to map them to the underlying relational database structure. These annotations denote the names of tables, columns, foreign keys, and information regarding relationships with other entities known as associations. When we execute a query with JPA, each row in the query will become an instance of the particular entity. It's also important to understand that entities work best with surrogate keys, so unique identifiers are created for each instance. Another key concept in the API is the EntityManager, which is the key interface for performing operations against the relational database. The EntityManager interface exposes a set of methods that accept entities or their IDs so they can be queried, inserted, updated, and deleted. Typically when working with the Java EE application server, the EntityManager is provided by the container and injected into beans as a dependency. So let's put it all together and introduce some more concepts. JPA applications are packaged with a persistence.xml file that provides configuration properties for the JPA provider and a definition of persistence units. The persistence unit is a logical grouping that contains metadata about the EntityManager, managed entities, and their associated mapping data. So just remember, the persistence unit contains all the information that can instruct an EntityManager on how to persist the entities into a relational database. An EntityManager is built using information in the persistence unit and associated with a persistence context. The persistence context contains the entity instances and manages their life cycle. Entities within the persistence context can then be persisted to the relational data store by the EntityManager. So that's an overview of how JPA works. Now let's talk a little bit more about JPQL. JPQL is very SQL-like, except the queries are written against the object model. Using JPQL, you can construct queries that perform select, update, and delete operations against the database. It's important to note the lack of support for insert operations with JPQL. Within JPQL queries, we can use corollaries for common relational functions like where clauses, like statements, parameters, aggregate operators, and even joins. Finally, let's talk about the CriteriaBuilder API. The CriteriaBuilder is limited to performing queries and is useful when a query needs to be dynamic such as when the where clause is built conditionally. Using the CriteriaBuilder for these situations is a little verbose, but it provides a type-safe way to build secure dynamic queries, which is a common requirement in applications. So that's a high-level look at JPA. Now we'll transition to the hands-on lessons to get some experience working with the API.

- The JPA API Supports Object-relational mapping (ORM) for Java applications with relational data.

- JPA Overview

  - JPA is just a Specification or API
  - The underlying implementation is build by JPA Providers (Most popular is Hibernate)
  - Hibernate - JPA Implementation provided by JBoss
  - JPA is typically broken down in 4 areas:
    - Object-relational mapping annotations
      - The JPA API provides support for key objects such as the EntityManager which is used
        to manage Entities.
    - Query Language (JPQL)
      - It allows us to write a SQL-like query that is Object-based
      - Work across Database providers
      - Totally irrevelant to the underlying data store
    - Criteria API
      - It provides a programmatic type-safe API for building queries against entities
      - Bit verbose to work with, but provides greater type safety

- Entities

  - A domain object that represents a table in a relational database.
    - Class Annotations: `@Entity`, `@Table`
    - Field/Method Annotations:
      - `@Id`, `@Column`, `@GeneratedValue`, `@JoinColumn`
      - `@OneToOne`, `@OneToMany`, `@ManyToMany`, `@ManyToOne`
    - Entity instances represent a row in the particular table
    - Annotations map entities to the relational model

- EntityManager

  - Manages entities withing a Persistence context
  - Provides an API for creating, updating, deleting, and querying entities from a Relational DB
  - Management by container or Application

- Persistence Context (`@PersistenceContext`)

  - Entity Instance
  - Entity Instance
  - Entity Instance

- Persistence Unit
  - Entity Manager Configuration
  - Entity Mapping
  - JPA Configuration

An EntityManager is built using information in the persistence unit and associated with a persistence context. The persistence context contains the entity instances and manages their life cycle. Entities within the persistence context can then be persisted to the relational data store by the EntityManager. So that's an overview of how JPA works.

- JPQL (Java Persistence Query Language)

  - SQL-like Query Language
  - Queries entities as opposed to the database schema
  - Allows for SELECT, UPDATE, and DELETE operations
  - Supports a subset of SQL commands

- Criteria Builder API

  - Type-safe API for entity operations
  - Useful for dynamic queries (Ex. Dynamic `where` clause)
  - Limited to query operations
  - Verbose approach to working with entities

- Association Concepts
  - Cardinality: `one-to-one`, `one-to-many`, `many-to-many`
  - Direction: whether associations exist on one side or both sides fo association entities
  - Cascading: whether an action on one entity cascades to its associated entities
  - Fetching: whether associations are fetched eagerly or lazily
