# Java Generate Unit Tests

## Task

**Generate comprehensive unit tests for Java code using JUnit 5 and Mockito**

This command analyzes existing Java classes and methods to create thorough unit test suites with proper mocking, edge cases, and assertions.

## Instructions

- Analyze the target Java class/method to understand its behavior and dependencies
- Generate JUnit 5 test classes with comprehensive test coverage
- Include proper mocking using Mockito for external dependencies
- Create tests for edge cases, error conditions, and boundary values
- Follow Java testing best practices and naming conventions
- Ensure tests are maintainable and well-documented

## Test Generation Strategy

1. **Code Analysis**: Examine the target class structure, dependencies, and functionality
2. **Test Structure**: Create organized test classes with descriptive test methods
3. **Mock Strategy**: Mock external dependencies, services, and repositories
4. **Test Cases**: Cover happy path, edge cases, error conditions, and boundary values
5. **Assertions**: Use JUnit 5 assertions and Hamcrest matchers for clarity
6. **Setup/Teardown**: Include proper @BeforeEach/@AfterEach for test isolation

## Test Categories to Generate

- **Unit Tests**: Test individual methods in isolation
- **Integration Tests**: Test class interactions with @SpringBootTest
- **Exception Testing**: Test error conditions and exception handling
- **Parameterized Tests**: Test multiple input combinations
- **Mock Verification**: Verify mock interactions and call counts
- **Edge Cases**: Boundary values, null inputs, empty collections

## JUnit 5 & Mockito Best Practices

1. **Descriptive Names**: Use clear, descriptive test method names
2. **AAA Pattern**: Arrange, Act, Assert structure
3. **Single Responsibility**: One logical assertion per test
4. **Mock Isolation**: Proper mocking to avoid external dependencies
5. **Test Data**: Use builders or factories for consistent test data
6. **Annotations**: Proper use of @Test, @Mock, @InjectMocks, etc.

## Output Format

```java
// TargetClassTest.java
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;
import static org.junit.jupiter.api.Assertions.*;
import static org.mockito.Mockito.*;

@ExtendWith(MockitoExtension.class)
class TargetClassTest {

    @Mock
    private DependencyService dependencyService;
    
    @InjectMocks
    private TargetClass targetClass;
    
    @BeforeEach
    void setUp() {
        // Common setup for all tests
    }
    
    @Test
    void shouldReturnExpectedResultWhenValidInput() {
        // Arrange
        String input = "valid input";
        String expected = "expected output";
        when(dependencyService.process(input)).thenReturn(expected);
        
        // Act
        String result = targetClass.processInput(input);
        
        // Assert
        assertEquals(expected, result);
        verify(dependencyService).process(input);
    }
    
    @Test
    void shouldThrowExceptionWhenNullInput() {
        // Arrange & Act & Assert
        IllegalArgumentException exception = assertThrows(
            IllegalArgumentException.class,
            () -> targetClass.processInput(null)
        );
        assertEquals("Input cannot be null", exception.getMessage());
    }
    
    @ParameterizedTest
    @ValueSource(strings = {"", " ", "   "})
    void shouldHandleEmptyOrBlankInput(String input) {
        // Act
        String result = targetClass.processInput(input);
        
        // Assert
        assertTrue(result.isEmpty());
    }
}
```

## File Structure

- Place test classes in `src/test/java` mirroring the source package structure
- Name test classes with `Test` suffix (e.g., `UserServiceTest`)
- Group related tests in nested test classes using `@Nested`
- Include test utilities and builders in separate utility classes

## Coverage Goals

- **Line Coverage**: 100% - Every line of code executed
- **Branch Coverage**: 100% - All conditional paths tested
- **Method Coverage**: 100% - All methods called in tests
- **Class Coverage**: 100% - All classes have test coverage

## Mock Patterns

```java
// Method mocking
when(mockService.methodName(anyString())).thenReturn("result");

// Void method verification
verify(mockService).voidMethod();

// Exception mocking
when(mockService.riskyMethod()).thenThrow(new RuntimeException("error"));

// Argument capturing
ArgumentCaptor<String> captor = ArgumentCaptor.forClass(String.class);
verify(mockService).method(captor.capture());
assertEquals("expected", captor.getValue());

// Multiple calls
when(mockService.method())
    .thenReturn("first")
    .thenReturn("second");
```

## Annotations Reference

- `@Test` - Marks a test method
- `@Mock` - Creates a mock instance
- `@InjectMocks` - Injects mocks into the test subject
- `@BeforeEach` - Setup before each test
- `@AfterEach` - Cleanup after each test
- `@ParameterizedTest` - Test with multiple parameters
- `@ValueSource` - Provides parameter values
- `@ExtendWith(MockitoExtension.class)` - Enables Mockito annotations

## Maven Dependencies

```xml
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter</artifactId>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-core</artifactId>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.mockito</groupId>
    <artifactId>mockito-junit-jupiter</artifactId>
    <scope>test</scope>
</dependency>
```