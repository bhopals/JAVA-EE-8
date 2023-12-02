### JSON-P (Java API for JSON Procesing)

JSON-P overview

The Java API for JSON processing, or JSON-P, is an API within Java EE that provides developers with additional support for working with JSON. Specifically, it provides support for parsing, generating, transforming, and querying JSON in Java applications. JSON-P contains two approaches JSON parsing and generation. One based on an object model and another based on a streaming model. The object model is a high-level API that is simple and easy to use. It provides the ability to read and create JSON using a key value based approach that is very similar to working with a map. While the object model is easier to use, it is not as efficient as the streaming-based API because objects are stored in memory. The streaming API is a low-level API designed to consume and produce large amounts of JSON using a parser based on an event model. It is more efficient because the processing avoids storing most of the JSON in memory. Additionally, within the API we'll find support for JSONPointer and JSONPatch. These allow us to traverse or modify sections of a JSON document with path-based expressions. Let's dive a little bit deeper into these approaches. Here we see an example of using the object model to build a JSON document. The object model uses a fluid builder API that allows us to easily chain message calls to build the two primary JSON structures, objects and arrays. Building a JSON object is pretty simple. We chain calls to the add method which accepts the property name as the first argument and the value as the second argument. You will notice objects can be nested within objects to build JSON documents, and the structure of our calls aligns to the format of a JSON document. Here we see an example of using the object model to read a JSON document. It uses a JSON reader to provide random access to properties using their property names. Similar to retrieving a value from a map with a key. When accessing property values, we have the option to access them via a JSON string for text values and a JSON number for numeric values. The JSON-P streaming API uses a different approach for working with JSON that is a little bit more verbose but more efficient. When using the streaming API to create a JSON object, we get a generator instance and then begin to write the object by invoking the write method with the property name and value as arguments. When using the generator, we need to explicitly start and end both objects and arrays. Let's now take a look at parsing using the streaming API. We'll use the same JSON document from the last slide in this example. When parsing using the streaming API, we must create a parser based off of a reader. From there, we use the parser to iterate the events in the JSON structure. If you look at the comments in the code you will see that as we iterate the object, we encounter different events that correspond with the document. The events indicate one of several types, including the start or close of an object or array, a key, or a value. If we want to retrieve a property name or value when iterating through the JSON, we can use several get methods that will type will type the value of that object at a particular location in the JSON structure. JSONPointer support is another feature found within the JSON-P API. It allows for easy access to JSON properties via a path-based expression, similar to how XPath can be used to access XML elements. So if we look at the JSON on the right, we can use our first expression to access the name property. Our second example illustrates how to traverse arrays using the expression. JSONPatch also uses the path-based expression approach. However, it uses it for modifications to the JSON document. Using JSONPatch, we can add, change, or remove properties on a JSON object.

- An API within JAVA EE that provides developers with additional support for working with JSON.
- It provides support for Parsing, Generating, Transforming, and Querying JSON in Java Apps.

- JSON-P contains two approaches in JSON Parsing and Generation

  - Object model-based API (HighLevel API) - Read and Create JSON using KEY-VAL approach
  - Streaming based API (Low-Level API)

- JSONPointer for property Access with Path Expressions (Similar to XPATH)
- JSONPatch for modifying JSON with Path Expressions

#### Object model-based API (HighLevel API)

- Read and Create JSON using KEY-VAL approach

- JSON-P features an object model API that allows us to perform various operations for the JSON data type within Java. Using the object model API, we can create, read, and string JSON objects and array structures using its interface which follows a builder pattern.

- `JsonObjectBuilder`
- `JsonArrayBuilder`
- `JsonWriterFactory`
- `StringWriter`
- `JsonWriter`

#### Streaming based API (Low-Level API)

- The JSON Processing API features a parser as part of the Streaming API. The parser can be used to efficiently read JSON objects using a poll model.

- `JsonParser`
- `Event`
- `JsonGenerator`

- The Json processing API features a JSON POINTER and JSON PATCH object that we can leverage when working with Json. The Json pointer allows us to use a string representing a path to a particular property in the Json to access the property value.
