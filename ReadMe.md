# cucumber-junit5-starter

This project serves as a starter template for Cucumber with JUnit 5. 
The purpose of this README is to document the purpose of each dependency included in the `pom.xml`, 
making it easier to remember and reuse for future projects.

### Dependency Management


    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.junit</groupId>
                <artifactId>junit-bom</artifactId>
                <version>5.11.0-M2</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <dependency>
                <groupId>io.cucumber</groupId>
                <artifactId>cucumber-bom</artifactId>
                <version>7.18.0</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
        </dependencies>
    </dependencyManagement>

junit-bom:

- Purpose: Ensures all JUnit dependencies use the same version (5.11.0-M2).
- Reason: Manages and synchronizes versions of all JUnit-related dependencies to prevent version conflicts.

cucumber-bom:

- Purpose: Ensures all Cucumber dependencies use the same version (7.18.0).
- Reason: Manages and synchronizes versions of all Cucumber-related dependencies to prevent version conflicts.

In summary, both dependencies are included to manage and synchronize the versions of their respective related dependencies,
ensuring compatibility and preventing conflicts.

/////


## Dependencies

### JUnit Jupiter

```xml
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <scope>test</scope>
</dependency>

- Purpose: Provides the JUnit 5 (Jupiter) testing framework.
- Features: Enables the use of annotations and features such as @Test, @BeforeEach, and @AfterEach.
- Scope: Test only; not included in production code.

In summary, this dependency allows you to write and execute tests using JUnit 5 in your project.

////


### cucumber-junit-platform-engine
### junit-platform-suite

    <dependency>
                <groupId>io.cucumber</groupId>
                <artifactId>cucumber-junit-platform-engine</artifactId>
                <scope>test</scope>
            </dependency>
    
            <dependency>
                <groupId>org.junit.platform</groupId>
                <artifactId>junit-platform-suite</artifactId>
                <scope>test</scope>
            </dependency>

### Execution of Cucumber Tests
The execution of the Cucumber tests in your project setup is handled by the JUnit Platform. 
Here's a detailed explanation addressing the specific questions:

### Who does the execution?

The execution is done by the JUnit Platform, specifically by the cucumber-junit-platform-engine dependency 
in conjunction with the junit-platform-suite dependency.

### How do they know that the @Suite tag is executable?

The @Suite annotation in JUnit 5 is used to specify that the annotated class is a test suite. 
The JUnit Platform recognizes and handles this annotation.

### Detailed Breakdown:
    JUnit Platform Execution:

The cucumber-junit-platform-engine provides the necessary integration for Cucumber to run on the JUnit Platform. 
When you run your tests, the JUnit Platform looks for test classes and methods that are 
annotated with JUnit 5 annotations (like @Suite).
The junit-platform-suite dependency allows you to define a suite of tests using the @Suite annotation.

    Recognition of @Suite Annotation:

The @Suite annotation, along with the configuration parameters provided (@SelectClasspathResource("features") 
and @ConfigurationParameter), tells the JUnit Platform where to find the feature files 
and how to configure the test execution.
The RunCucumberTest class is annotated with @Suite, which the JUnit Platform scans to identify as an entry point 
for executing the suite of tests.
@SelectClasspathResource("features") specifies the location of the Cucumber feature files.
@ConfigurationParameter(key = PLUGIN_PROPERTY_NAME, value = "pretty") sets a configuration parameter 
for the Cucumber test execution.

### Summary:
The JUnit Platform (through cucumber-junit-platform-engine and junit-platform-suite dependencies) is responsible 
for the execution of your Cucumber tests.
It recognizes the @Suite annotation on your RunCucumberTest class and uses the provided configuration 
to locate and run the tests.
By ensuring that your pom.xml includes the necessary dependencies and that your test class is correctly annotated, 
the JUnit Platform can execute your Cucumber tests seamlessly.

///

### Cucumber Java

```xml
<dependency>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-java</artifactId>
</dependency>

- Purpose: Provides the Cucumber framework support for Java.
- Features: Allows you to write step definitions in Java for your Cucumber feature files.
- Scope: This dependency is essential for integrating Cucumber with Java, 
enabling the execution of feature files and mapping them to Java code.


///

Summary:
The JUnit Platform (through cucumber-junit-platform-engine and junit-platform-suite dependencies) is responsible 
for the execution of your Cucumber tests. It recognizes the @Suite annotation on your RunCucumberTest class 
and uses the provided configuration to locate and run the tests. 
By ensuring that your pom.xml includes the necessary dependencies and that your test class is correctly annotated, 
the JUnit Platform can execute your Cucumber tests seamlessly.

This README should help you remember the purpose of each dependency 
and how they contribute to the Cucumber-JUnit 5 setup in your projects.

