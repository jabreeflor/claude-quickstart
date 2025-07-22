# Maven Test Coverage Command

This command runs Maven tests with coverage reporting using JaCoCo and provides analysis of test results.

## Purpose
Execute the full Maven test suite, generate JaCoCo coverage reports, and analyze test results to identify areas needing attention.

## Usage
Type `/mavenTest` in Claude Code to execute this command.

## Action
When this command is executed, Claude should:

1. **Check Maven Setup**: Verify pom.xml exists and JaCoCo plugin is configured
2. **Run Tests with Coverage**: Execute `mvn clean test jacoco:report` or `mvn clean verify`
3. **Analyze Results**: Review test output for:
   - Passing/failing tests
   - Test execution time
   - Coverage percentages (instruction, branch, line, complexity, method, class)
4. **Generate Coverage Report**: Ensure HTML coverage report is created in `target/site/jacoco/`
5. **Identify Issues**: Highlight:
   - Failed tests with error details
   - Any coverage below 100%
   - Uncovered critical classes/methods
   - Slow-running tests
6. **Provide Recommendations**: Suggest:
   - Classes that need more test coverage
   - Types of tests to add (unit, integration, edge cases)
   - Performance improvements for slow tests
7. **Summary Report**: Present coverage metrics and actionable insights

## Coverage Analysis
- **Instruction Coverage**: Target 100% coverage
- **Branch Coverage**: Target 100% coverage - ensure all conditional paths are tested
- **Line Coverage**: Target 100% coverage - verify all code lines are executed
- **Method Coverage**: Target 100% coverage - check all methods are tested
- **Class Coverage**: Target 100% coverage - ensure all classes have tests

## Output Format
```
☕ Maven Test Results Summary
✅ Passed: X tests
❌ Failed: Y tests
⏱️  Duration: Z seconds

📊 JaCoCo Coverage Report
Instructions: XX% (target: 100%)
Branches: XX% (target: 100%)
Lines: XX% (target: 100%)
Methods: XX% (target: 100%)
Classes: XX% (target: 100%)

🎯 Action Items:
- Add tests for: [uncovered classes]
- Fix failing: [test names]
- Improve coverage in: [specific packages/methods]
```

## Alternative Commands
- If basic command doesn't work, try:
  - `mvn clean test jacoco:report jacoco:check`
  - `mvn clean verify` (if verify goal includes tests)
  - `./mvnw clean test jacoco:report` (if using Maven wrapper)

## JaCoCo Setup Check
If JaCoCo is not configured, suggest adding to pom.xml:
```xml
<plugin>
    <groupId>org.jacoco</groupId>
    <artifactId>jacoco-maven-plugin</artifactId>
    <version>0.8.7</version>
    <executions>
        <execution>
            <goals>
                <goal>prepare-agent</goal>
            </goals>
        </execution>
        <execution>
            <id>report</id>
            <phase>test</phase>
            <goals>
                <goal>report</goal>
            </goals>
        </execution>
    </executions>
</plugin>
```

## Error Handling
- If Maven is not installed, suggest installation steps
- If tests fail, show detailed error messages and stack traces
- If coverage is below 100%, highlight specific classes/methods needing attention
- If no tests exist, recommend creating a basic test structure with JUnit 5