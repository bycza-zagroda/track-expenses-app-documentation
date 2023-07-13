# Testing the code

## Naming Conventions in Tests: A Guide for Developers

Naming conventions in tests are important for writing code that is easy to read and maintain. Good test names should
convey what the test does and what it is testing, and should follow a consistent style throughout your codebase.

In this article, we will discuss some naming conventions that can help you write better tests.
General Naming Conventions

When naming your tests, keep in mind that the name should be descriptive and convey the purpose of the test. Here are
some general naming conventions to follow:

    Use descriptive names that explain what the test does.
    Use underscores to separate words in the name.
    Begin the name of the test with a verb that describes what it is testing, such as "should" or "must".
    Use clear and concise language.
    Use a consistent naming style throughout your codebase.

For example, if you are testing a function that calculates the sum of two numbers, a good name for the test might be:

```java
@DisplayName("Appropriate description of the test")
@Test
public void testXXX_WhenXXX_ThenXXX() {
   // Test code here
}
```

## Given-When-Then Naming Conventions

Another popular naming convention for tests is the "Given-When-Then" style. This style breaks down the test into three
parts:

    Given: The initial state or conditions of the system.
    When: The action or event being tested.
    Then: The expected result or outcome of the test.

This style can be very useful for complex tests that have multiple steps. Here's an example:

```java
@DisplayName("Appropriate description of the test")
@Test
public void givenValidUser_whenLogin_thenUserIsAuthenticated(){
   // Test code here
}
```

In this test, the "Given" part is the valid user, the "When" part is the login action, and the "Then" part is the
expected result of the user being authenticated.
Testing Exceptions

When testing exceptions, it is important to include the word "throws" in the test name, followed by the name of the
exception being thrown. Here's an example:

```java
@DisplayName("Appropriate description of the test")
@Test
public void shouldThrowExceptionWhenInputIsNull(){
   // Test code here
}
```

In this test, we are testing whether an exception is thrown when the input is null.
Conclusion

Naming conventions in tests are important for writing code that is easy to read and maintain. By following these
conventions, you can create test names that are descriptive and convey the purpose of the test. This will help you and
other developers working on the codebase understand what the tests are doing and how they are testing the code.

## Good Practices in Testing with Spring Boot

Testing is an essential part of software development, and in Spring Boot applications, testing is even more critical due
to the complexity of the framework. Here are some good practices to follow when testing your Spring Boot applications:

1. Use Test-Driven Development (TDD)

Test-Driven Development (TDD) is a development approach that requires writing tests before writing any production code.
This approach ensures that the code is well-tested and that all requirements are met. With TDD, you start by writing a
test that fails, then you write just enough production code to pass the test. This cycle is repeated until all
requirements are met.

2. Write Clear and Descriptive Tests

Writing clear and descriptive tests is essential for maintaining and understanding your test code. Use descriptive names
for your test methods and follow the naming conventions discussed in the previous section. Also, use comments to
describe the purpose of the test and what it is testing.

3. Test All Components

In Spring Boot applications, there are many components, such as controllers, services, and repositories. It is essential
to test all components to ensure that they are working correctly. Use unit tests to test individual components and
integration tests to test the interactions between different components.

4. Use Mocks and Stubs

Mocks and stubs are tools that allow you to test your code in isolation. Use mocks to simulate the behavior of external
dependencies and stubs to provide fake data to your tests. This approach allows you to test your code in a controlled
environment and ensures that your tests are not affected by external factors.

5. Use Test Annotations

Spring Boot provides many annotations that can be used to write tests. Use these annotations to configure your tests,
such as @RunWith to specify the test runner, @Mock to create a mock object, and @Test to mark a test method. These
annotations make it easy to write tests and ensure that your tests are well-organized and readable.

6. Automate Your Tests

Automating your tests is essential for ensuring that they are run consistently and that you can quickly detect and fix
any issues. Use a continuous integration tool, such as Jenkins or Travis CI, to automate your tests and run them after
every code change. This approach ensures that you catch any issues early in the development process.

7. Use Code Coverage Tools

Code coverage tools are used to measure the amount of code that is covered by your tests. Use code coverage tools to
ensure that your tests cover all parts of your codebase. A high code coverage percentage indicates that your code is
well-tested and that there are no untested parts.

By following these good practices, you can ensure that your Spring Boot applications are well-tested and free of bugs.
Testing is a critical part of the development process, and by investing time and effort in testing, you can ensure that
your code is of the highest quality.

## Display Names
Test classes and test methods can declare custom display names via `@DisplayName` — with spaces, special characters, and even emojis — that will be displayed in test reports and by test runners and IDEs.

Adnotacja DisplayName w testach Java służy do nadania czytelnej nazwy testowi, która będzie wyświetlana podczas uruchamiania testów. Wartość tej adnotacji powinna być krótkim, opisowym opisem testu. Powinna być jasna i zwięzła, aby pomóc użytkownikowi w identyfikacji testu i jego funkcjonalności.

```java
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;

@DisplayName("A special test case")
class DisplayNameDemo {

    @DisplayName("Custom test name containing spaces")
    @Test
    void testWithDisplayNameContainingSpaces() {
    }
    
    // ...
}
```

## Links
- [JUnit 5 User Guide - writing tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests)
- [JUnit 5 User Guide - writing tests - display-names](https://junit.org/junit5/docs/current/user-guide/#writing-tests-display-names)
- [JUnit 5 User Guide - writing tests - parameterized tests](https://junit.org/junit5/docs/current/user-guide/#writing-tests-parameterized-tests)
- [Given When Then in Java](https://www.javacodegeeks.com/2015/01/given-when-then-in-java.html)
- [Given When Then w testach](https://javastart.pl/baza-wiedzy/testowanie-jednostkowe/given-when-then-w-testach)
- [Lambda Behave - A modern testing and behavioural specification framework for Java 8](http://richardwarburton.github.io/lambda-behave/)
