### Security API

- The Java EE Security API is a new API introduced in Java EE 8 that simplifies and standardizes the security model. The Security API was introduced as part of JSR 375. It was meant to build a better security model that is portable across several Java EE technologies. The API takes an annotation-based approach, eliminating the need for configuration to be placed in a web.xml file moving forward. Prior to the Security API, container providers defined their own implementations which contain differing concepts and terminology. This made it difficult for developers to implement security. The changes introduced in the Security API allow security to be applied uniformly across containers for servlets and EJB. The first new interface introduced by the Security API that we'll cover is the HttpAuthenticationMechanism. It defines an interface for building authentication mechanisms that can be deployed using CDI. So, basically, this is a component that confirms the identity of a user, given their provided credentials. Within the Security API, there are three implementations provided out of the box that can be leveraged by developers. If none of the implementations are sufficient, developers can build their own implementation of the interface. The three built-in implementations of the HttpAuthenticationMechanism support basic, form, and a custom form authentication mechanism. On the interface, we find three methods, the most important of which is validateRequest, which is used to authenticate the caller. Another interface introduced by the Security API is the IdentityStore. The IdentityStore provides a uniform approach to working with stores of user credentials. So, typically we store credentials in something like a database or an LDAP, and the IdentityStore abstracts those user credential stores. The final major interface introduced by the Java EE Security API is the SecurityContext. It provides convenient access to information about the authenticated user within servlets and EJBs. Currently, servlets and EJBs have inconsistent approaches to obtaining the authenticated user and determining if they have specific roles. This inconsistency is remediated by the SecurityContext. Methods on the SecurityContext interface allow application code to retrieve user principles, check access to web resources, and determine if a caller has a particular role.

- Security API

  - JAVA EE Security API simplifies and Standardize the Security Model
  - Establishes a simple and standard model for JAVA EE security model
  - Provides an annotation-based approach to security configuration
  - Establish uniform security across container for Servlet and EJB

- 3 Interfaces (`HttpAuthenticationMechanism`, `IdentityStore`, `SecurityContext`)

  - 1. HttpAuthenticationMechanism

    - Standardizes authentication in Web Application
    - Defines an interface for Authentication mechanism
    - API Defines three built-in implementations
    - Allows for development of custom authentication mechanism

    - 3 built-in Implimentations of HttpAuthenticationMechanism
      - BasicAuthenticationMechanismDefinition - implements basic authentication
      - FormAuthenticationMechanismDefinition - implements form authentication
      - CustomAuthenticationMechanismDefinition - Implments custom form authentication
    - Methods
      - `validateRequest()`
      - `secureResponse()`
      - `cleanSubject()`

  - 2. IdentityStore

    - Standardizes interaction with identity stores
    - Abstracts usage of credential stores such as LDAPs
    - API defines two built-in implementations: LDAP, Database
    - Allow for development of custom identity stores

  - 3. SecurityContext
    - Provides information about the authenticated user within the Servlet and EJB
    - Remedies inconsistencies between Servlet and EJB Security
      - This Interface helps Servlet and EJB to retrieve current authenticated user details,
        role, access, etc details.
    - Allows interaction between application code and Security API
