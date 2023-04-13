# Unit tests

**Unit testing** refers to the testing of individual components in the source code, such as classes and their provided methods. The writing of tests reveals whether each class and method observes or deviates from the guideline of each method and class having a single, clear responsibility.

## Unit Test Example

```java
public class CalculatorTest {

    private Calculator calculator;

    @Before
    public void setUp() {
        calculator = new Calculator();
    }

    @DisplayName("When the two numbers are added the result will be correct")
    @Test
    public void whenAddTwoNumbers_thenCorrectResult() {
        int result = calculator.add(2, 3);
        assertThat(result).isEqualTo(5);
    }

    @DisplayName("When two numbers are subtracted, the result will be correct")
    @Test
    public void whenSubtractTwoNumbers_thenCorrectResult() {
        int result = calculator.subtract(5, 3);
        assertThat(result).isEqualTo(2);
    }
}
```

This unit test tests the Calculator class's add() and subtract() methods. The test creates an instance of the Calculator
class in the setUp() method and tests each method independently. The test ensures that the methods return the correct
results for the given input.

This test example follow good practices for testing in Spring Boot. The unit test tests a single class's methods in isolation. 
The tests are well-organized, use descriptive names, and ensure that the code is well-tested.

## Links
- [Spring Boot Integration Test with TDD | JUnit5 & H2 | JavaTechie](https://www.youtube.com/watch?v=Hh17JDpsKqc)


