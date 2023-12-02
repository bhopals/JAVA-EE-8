#### Bean Validation

Validation of data is frequently performed within application to ensure data provided by a user or another system meets certain requirements. These constraints are important for ensuring the integrity of the system's data and can aid in the application of security. The Java EE Bean Validation API provides a simple, annotation-based approach that allows developers to add validation constraints on beans. The Bean Validation API was introduced in Java EE 6 and has received several updates as part of Java EE 8. Within the Bean Validation API, we'll find several annotations that provide built-in restraints for common validations. For more complex, or frequently used validations, the API allows developers to build their own custom constraints. The constraints can be applied on various elements of a class, such as fields, methods, constructors, method parameters, and other annotations. Applying constraints on beans provides a single source of validation that is integrated with various Java EE technologies to avoid duplication of validation logic. Java EE 8 implementations will adhere to Bean Validation 2.0, which added several features. First, there were additional built-in constraints added to the API which are quite useful. I'll show you these in a minute. The new version also allows validation to be applied on objects within container types, such as Lists and Maps. This also includes the keys of a map. The API also introduced support for new Java 8 types, such as optional and the new date/time data types. Within the API, you will find support for 28 built-in constraints seen over the following slides. The bolded annotations indicated built-in constraints that were added in Java EE 8. We won't discuss each of these in detail, but you can see there are constraints for null checks, Boolean validation, and numeric validation. The built-in annotations also contain support for checks on dates. I should also point out the Pattern annotation, which is very powerful because it allows a regular expression to be used for validation. So you can supply your own RegExs, which makes it extremely flexible for putting constraints on fields. Finally, you will notice support for e-mail, which is extremely important, and that was introduced in Java EE 8. Here is an example of several constraints applied at the field level on a simple student class. The example shows the ability to add multiple constraints on a field, such as the E-mail field, which ensures the field is not null and contains a valid e-mail address. You will also notice that some constraint annotations, such as the Size annotation on the Aliases field, require additional information to be supplied in the elements of the annotation. Additionally, we are able to apply constraints on the generic type arguments of the Alias list to ensure the elements of the list are not empty. The Bean Validation API also provides support for constraint groups, which can be used to only apply certain constraints on an object. Here we see a Constraint group that restricts the age of college students to 18 and grade school students to five. This allows our validation to be applied for a particular context or situation within our application.

- Bean Validation API

  - Features built-in constraints (Annotation Based)
  - Allow custom validators to be created
  - Applied on fields, methods, constructors, parameters, types and annotations

- What's New in Bean Validations 2.0

  - New built-in constraints
  - Cascade validation to container types
  - Support for java 8 Optional, Date time data types

- Built-in Constraints

  - `@Null`
  - `@NotNull`
  - `@AssertTrue`
  - `@AssertFalse`
  - `@Min`
  - `@Max`
  - `@DecimalMin`
  - `@DecimalMax`
  - `@Negative`
  - `@NegativeOrZero`
  - `@Positive`
  - `@PositiveOrZero`
  - `@Pattern`
  - `@Size`
  - `@Digits`
  - `@Past`
  - `@PastOrPresent`
  - `@Future`
  - `@FutureOrPresent`
  - `@Pattern`
  - `@NotEmpty`
  - `@NotBlank`
  - `@Email`

- Custom Validation Annotations
- Custom Constraint Validators
  - Create @Interface
  - Class needs to implement ConstraintValidator
  - `isValid` method
