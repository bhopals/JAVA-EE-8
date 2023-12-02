### Servlets

- Servlet runs in a Servlet container which is a web or application server that provides network
  services for receiving requests and sending responses.

- All Java EE application servers support the servlet spec and contain a servlet
  container where servlets can be initialized.

- Once initialized, a servlet is available for processing requests, which are typically HTTP requests sent by the web browser. Requests are processed using a servlet interface method (doGet, doPost, doPut, doDelete) that corresponds to the HTTP method(GET, POST, PUT, DELETE) of the request and then dynamic content is generated and sent to the browser.

#### Servlet API

- Component for processing web requests
- Provides request-handling HTTP methods like GET, or POST
- Allows dynamic content in web applications
- Annotation-based configuration
- Asynchronous processing of requests

- The main benefit of the Servlet API is the abstraction it provides over low-level interfaces for networking and request parsing, making it easier for Java developers to build web applications. Here you see an example of a servlet in its simple

#### JSP (JAVA SERVER PAGES)

JavaServer Pages, or JSP, is a Java EE technology that allows developers to easily build web pages with dynamic content. Most web pages are built using Dynamic Content because it allows unique experiences for each visit or visitor to a page.

A browser passes HTTP requests to a servlet. Which performs its logic and then stores data into a model. The servlet then passes the request to the JSP. Which extracts the data from the model and intermixes it within a template to generate a dynamic page for the end user. The pattern known as Model View Controller, or MVC for short, separates the three primary concerns of building dynamic web pages to prevent code from becoming unreadable and hard to maintain.

- Support Tag libraries and expression language

- JSP Constructs

  - Directives - Instruct the container how to translate the page

    - `<%@ include [fragment] %>`
    - `<%@ page %>`
    - `<%@ taglib %>`

  - Expression Language - `${expression}`
  - Expressions - Allow an evaluated expression to be written as output to a page - `<%= [EXPRESSION] %>`
  - Scriptlets - Allow Java code in a JSP file - `<% [CODE] %>`
  - Declaration - Declare a variable inside the JSP or corresponding servlet - `<% [VARIABLE] %>`

#### JSF (JAVA SERVER FACES)

Java Server Faces is a java based web application framework that simplifies the development of web based applications. JSF provides a more cohesive model than servlets and JSP for building web apps. It's model includes a server side UI component framework, templating support and the ability to bind UI components to java pojos known as backing beans.

- JSF Components
  - Faces Servlet - Manages the request-processing lifecycle for JSF applications
  - Facelet -(JSP Pages/View) - Views featuring a component tree that corresponds to the user interface
  - Component - Server-side UI Components corresponding to HTML components that render on the browser
  - Backing Beans - CDI Beans with fields and methods that bind to component data and actions
  - Event Handlers - Methods on backing bean bound to component actions

When a browser passes HTTP request to the faces servlet, it will build a component tree for the facelet identified by the URL. Then components in the component tree will have their values updated with corresponding information found in the request and the values will be validated. After validation, component values will update fields in the manage bean they are bound to with their values. Next, the face's servlet will invoke any action methods on the managed bean, the action methods will ultimately return a string which indicates the next facelet to render. The facelet bean returned will have its component tree updated with values from any backing bean it references and then its component tree will be written as HTML returned to the browser. So, just a recap, JSF is a java EE web application framework that is based upon MVC principles, within the technology we find a life cycle that orchestrates the request processing which involves a sequence of steps to bind server facelet components to pojo based backing beans. Within JSF, we'll also find a wide variety of component libraries such as prime faces.

#### KEYWORDS

- THREAD STARVATION
- ASYNCHRONOUS Servlet to alleviate THREAD STARVATION
