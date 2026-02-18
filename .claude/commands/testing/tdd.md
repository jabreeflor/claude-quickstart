# Test-Driven Development (TDD)

Enforce strict RED-GREEN-REFACTOR workflow for implementing **$ARGUMENTS**

## The Iron Rules

1. **NO production code without a failing test first**
2. **Write the MINIMUM code to pass the test**
3. **Refactor only when tests are green**
4. **Commit after each green**

## Workflow

### 🔴 RED Phase
1. Write a single failing test that describes the desired behavior
2. Run the test — **it MUST fail**
3. If it passes, the test is wrong or the feature already exists
4. Failure message should clearly indicate what's missing

### 🟢 GREEN Phase  
1. Write the **minimum** code to make the test pass
2. No extra features, no "while I'm here" additions
3. Ugly code is fine — we'll fix it in refactor
4. Run tests — they MUST pass

### 🔵 REFACTOR Phase
1. Tests are green — now improve the code
2. Remove duplication, improve naming, simplify
3. Run tests after each change — stay green
4. Commit when satisfied

## Anti-Patterns to Avoid

❌ **Writing tests after code** — You lose the design benefits  
❌ **Multiple features per cycle** — One behavior at a time  
❌ **Skipping the red phase** — If it doesn't fail first, you don't know it works  
❌ **Gold-plating in green** — Save improvements for refactor  
❌ **Refactoring while red** — Fix the test first  
❌ **Testing implementation details** — Test behavior, not internals

## Test Structure

```
// Arrange - Set up the test scenario
// Act - Execute the behavior under test  
// Assert - Verify the expected outcome
```

## Commands to Run

```bash
# Watch mode (recommended)
npm test -- --watch

# Single run
npm test

# With coverage
npm test -- --coverage
```

## Cycle Checklist

For each feature/behavior:

- [ ] Write failing test describing the behavior
- [ ] See test fail with clear message
- [ ] Write minimum code to pass
- [ ] See test pass
- [ ] Refactor if needed (stay green)
- [ ] Commit: `git commit -m "feat: [behavior description]"`

## Example Cycle

**Task:** Add a function that doubles a number

```
🔴 RED:
test('doubles positive numbers', () => {
  expect(double(5)).toBe(10);
});
// ReferenceError: double is not defined ✓

🟢 GREEN:
function double(n) {
  return 10;  // Minimum to pass THIS test
}
// Test passes ✓

🔴 RED (next case):
test('doubles negative numbers', () => {
  expect(double(-3)).toBe(-6);
});
// Expected -6, got 10 ✓

🟢 GREEN:
function double(n) {
  return n * 2;  // Now we generalize
}
// All tests pass ✓

🔵 REFACTOR:
// Code is already clean, commit!
```

## Start Now

Begin implementing **$ARGUMENTS** using strict TDD:

1. What's the first behavior to test?
2. Write that test
3. Watch it fail
4. Make it pass
5. Repeat
