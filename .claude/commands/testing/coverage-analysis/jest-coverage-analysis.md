# Test Coverage Command

This command runs Jest tests with coverage reporting and provides analysis of test results.

## Purpose
Execute the full Jest test suite, generate coverage reports, and analyze test results to identify areas needing attention.

## Usage
Type `/jest` in Claude Code to execute this command.

## Action
When this command is executed, Claude should:

1. **Check Test Setup**: Verify Jest configuration exists (jest.config.js, package.json)
2. **Run Tests with Coverage**: Execute `npm test -- --coverage` or `npx jest --coverage`
3. **Analyze Results**: Review test output for:
   - Passing/failing tests
   - Test execution time
   - Coverage percentages (statements, branches, functions, lines)
4. **Generate Coverage Report**: Ensure HTML coverage report is created
5. **Identify Issues**: Highlight:
   - Failed tests with error details
   - Any coverage below 100%
   - Uncovered critical files
   - Slow-running tests (> 1s)
6. **Provide Recommendations**: Suggest:
   - Files that need more test coverage
   - Types of tests to add (unit, integration, edge cases)
   - Performance improvements for slow tests
7. **Summary Report**: Present coverage metrics and actionable insights

## Coverage Analysis
- **Statements**: Target 100% coverage
- **Branches**: Target 100% coverage - ensure all conditional paths are tested
- **Functions**: Target 100% coverage - verify all exported functions have tests
- **Lines**: Target 100% coverage - check for untested code paths

## Output Format
```
🧪 Test Results Summary
✅ Passed: X tests
❌ Failed: Y tests
⏱️  Duration: Z seconds

📊 Coverage Report
Statements: XX% (target: 100%)
Branches: XX% (target: 100%)
Functions: XX% (target: 100%)
Lines: XX% (target: 100%)

🎯 Action Items:
- Add tests for: [uncovered files]
- Fix failing: [test names]
- Improve coverage in: [specific areas]
```

## Alternative Commands
- If `npm test` doesn't work, try:
  - `yarn test --coverage`
  - `pnpm test -- --coverage`
  - `npx jest --coverage --verbose`

## Error Handling
- If Jest is not configured, suggest setup steps
- If tests fail, show detailed error messages
- If coverage is below 100%, highlight specific files needing attention
- If no tests exist, recommend creating a basic test structure