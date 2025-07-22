# Jest Generate Unit Tests

## Task

**Generate comprehensive unit tests for JavaScript/TypeScript code using Jest framework**

This command analyzes existing code and creates thorough unit test suites with proper mocking, edge cases, and assertions.

## Instructions

- Analyze the target file/function to understand its behavior and dependencies
- Generate Jest test files with comprehensive test coverage
- Include proper mocking for external dependencies and modules
- Create tests for edge cases, error conditions, and boundary values
- Follow Jest best practices and naming conventions
- Ensure tests are maintainable and well-documented

## Test Generation Strategy

1. **Code Analysis**: Examine the target code structure, dependencies, and functionality
2. **Test Structure**: Create organized test suites with descriptive `describe` blocks
3. **Mock Strategy**: Mock external dependencies, APIs, and file system operations
4. **Test Cases**: Cover happy path, edge cases, error conditions, and boundary values
5. **Assertions**: Use appropriate Jest matchers for clear, meaningful assertions
6. **Setup/Teardown**: Include proper beforeEach/afterEach for test isolation

## Test Categories to Generate

- **Unit Tests**: Test individual functions in isolation
- **Integration Tests**: Test component interactions
- **Error Handling**: Test error conditions and edge cases
- **Async Testing**: Proper handling of promises and async/await
- **Mock Testing**: Verify function calls and mock interactions
- **Edge Cases**: Boundary values, null/undefined, empty inputs

## Jest Best Practices

1. **Descriptive Names**: Use clear, descriptive test names
2. **AAA Pattern**: Arrange, Act, Assert structure
3. **Single Responsibility**: One assertion per test when possible
4. **Mock Isolation**: Proper mocking to avoid external dependencies
5. **Test Data**: Use factories or fixtures for consistent test data
6. **Async Handling**: Proper async/await or return promise patterns

## Output Format

```javascript
// target-file.test.js
import { functionName, ClassName } from './target-file';
import { mockDependency } from './mocks';

// Mock external dependencies
jest.mock('./external-dependency');

describe('functionName', () => {
  beforeEach(() => {
    jest.clearAllMocks();
  });

  describe('happy path', () => {
    it('should return expected result for valid input', () => {
      // Arrange
      const input = 'valid input';
      const expected = 'expected output';
      
      // Act
      const result = functionName(input);
      
      // Assert
      expect(result).toBe(expected);
    });
  });

  describe('edge cases', () => {
    it('should handle null input gracefully', () => {
      expect(() => functionName(null)).toThrow('Expected error message');
    });
    
    it('should handle empty input', () => {
      const result = functionName('');
      expect(result).toBe('');
    });
  });

  describe('error conditions', () => {
    it('should throw error for invalid input', () => {
      expect(() => functionName(invalidInput)).toThrow();
    });
  });
});
```

## File Structure

- Place test files adjacent to source files with `.test.js` or `.spec.js` extension
- Mirror the source directory structure in `__tests__` directory if preferred
- Include setup files for common mocks and test utilities
- Create `jest.config.js` if custom configuration is needed

## Coverage Goals

- **Statements**: 100% - Every line of code executed
- **Branches**: 100% - All conditional paths tested
- **Functions**: 100% - All functions called in tests
- **Lines**: 100% - All executable lines covered

## Mock Patterns

```javascript
// Module mocks
jest.mock('./api-client');

// Function mocks
const mockFunction = jest.fn();

// Class mocks
jest.mock('./MyClass', () => {
  return jest.fn().mockImplementation(() => {
    return { method: jest.fn() };
  });
});

// Async mocks
mockAsyncFunction.mockResolvedValue('success');
mockAsyncFunction.mockRejectedValue(new Error('failure'));
```