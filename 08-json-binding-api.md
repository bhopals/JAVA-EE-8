### JSON-B (Java API for JSON Binding)

The Java API for JSON binding, known as JSON-B, is an API for converting Java objects to and from JSON. It helps Java developers working with JSON in their applications to be quickly able to convert back and forth from JSON to POJOs. JSON-B is a very focused, yet powerful API that simplifies working with JSON for Java EE developers. The API allows Java objects to be easily serialized into a JSON string. Additionally, the API allows JSON strings to be deserialized into a Java object. It performs these conversions by mapping JSON properties to Java fields and then converting them based upon the data type. Within the API is a set of annotations that allow developers to customize the mappings to meet the requirements. So when we think about serialization and deserialization, this is what it looks like. We have a Java object with fields on the left and a JSON object with properties on the right. You will notice the correlation between the field and property names, which is how JSON-B does the translation. If subtle differences exist or a different JSON representation is preferred, JSON-B provides a set of annotations to customize the mappings. JSON-B supports mapping for a wide array of types found in Java. Its coverage includes basic primitive types, custom POJOs, dates, classes, collections, arrays, and enumerations. Within JSON-B, we are able to customize a large number of the mapping configurations to support special situations. Primarily using an annotation-based approach, we are able to change property names, orders, and account for the absence of a property. Additionally, the annotations allow us to provide mapping strategies for fields, such as numerics or dates that may have slightly different formats in JSON.

- To converting JAVA Objects TO and FROM JSON
- Convert Back and Forth from JSON to POJO
- JSON-B is very Powerful JAVA EE API that simplifies working with JSON

- JSON-B

  - Provides serialization of Java Objects to JSON
  - Provides deserialization of JSON to Java Objects
  - It Perform these conversions by mapping JSON Properties to Java Fields and then
    converting them based upon the data type
  - Contains a set of Annotations for Customizing mappings

- JSON-B Mapping

  - Basic Types
  - Dates
  - Classes
  - Collections
  - Arrays
  - Enumerations

- Mapping Customizations

  - Property Names
  - Property Orders
  - Ignoring Properties
  - Null Values
  - Number formats
  - Date formats
  - Binary

- `JsonbConfig` - To provide Configuration to JSON-B
