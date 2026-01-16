# Unit Test Generation Task

I need comprehensive unit tests for [CLASS_NAME/MODULE_NAME] using JUnit and Mockito.

## Context
- Language: Java
- Testing Framework: JUnit 5
- Mocking Framework: Mockito
- Code to test: [provide file path or paste code]

## Test Generation Approach

### Step 1: Finite State Machine Analysis
First, analyze the code and:
1. Identify all states the system can be in
2. List all possible state transitions
3. Document guard conditions (what must be true for transitions)
4. Define invariants (conditions that must always hold)
5. Map out edge cases and boundary conditions

Present this FSM analysis for my review before proceeding.

### Step 2: Test Case Design
For each element identified above, design test cases that cover:
- **State Coverage**: Every reachable state
- **Transition Coverage**: Every valid transition between states
- **Guard Validation**: Transitions blocked when guards fail
- **Invariant Verification**: Invariants hold before/after all operations
- **Edge Cases**: Boundary values, null handling, empty collections
- **Error Paths**: Exception scenarios and failure modes

### Step 3: Implementation Guidelines

**Mocking Strategy - Follow These Rules:**

MOCK when:
- External dependencies (databases, APIs, file systems, network calls)
- Non-deterministic behavior (random, time-based, UUIDs)
- Slow operations that would make tests sluggish
- Dependencies that require complex setup
- Testing error handling from dependencies

DO NOT MOCK when:
- Testing interactions between classes that are core business logic
- Simple data objects (DTOs, entities, value objects)
- The class under test itself
- Collaborators where the interaction IS what you're testing
- Standard library classes (List, Map, String, etc.)

**Test Quality Requirements:**
- Each test should verify ONE specific behavior/scenario
- Test names should clearly describe what is being tested: `should[ExpectedBehavior]When[Condition]`
- Use AAA pattern: Arrange, Act, Assert
- Avoid testing implementation details - focus on observable behavior
- No trivial tests (e.g., testing getters/setters only)
- Include assertion messages that explain what failed
- Verify state changes, not just method calls
- For void methods, verify side effects or state changes

**Additional Requirements:**
- Use `@BeforeEach` for common setup, but keep tests independently readable
- Prefer real objects over mocks when reasonable
- When mocking, verify meaningful interactions, not just "was called"
- Include both positive and negative test cases
- Test boundary conditions explicitly
- Add `@DisplayName` annotations for complex scenarios
- Consider parameterized tests for similar scenarios with different inputs

## Mocking Decision Framework

For each dependency, ask:
1. **Is it infrastructure?** → MOCK (database, HTTP client, file system)
2. **Is it business logic?** → DON'T MOCK (use real implementation or refactor)
3. **Is the interaction the test subject?** → DON'T MOCK (integration point being tested)
4. **Does it make tests slow/flaky?** → MOCK
5. **Is it a value object/DTO?** → DON'T MOCK (use real instances)

When you DO mock:
- Verify meaningful behavior, not just "method was called"
- Use argument captors to verify complex interactions
- Prefer `verify()` with specific arguments over `any()`

When you DON'T mock:
- Create real instances with valid test data
- Consider test builders/factories for complex objects
- Use in-memory implementations where available (e.g., in-memory databases for repositories)

## Deliverables
1. FSM analysis document (for review)
2. Test case design matrix showing coverage
3. Fully implemented test class with:
   - Proper setup/teardown
   - Well-organized test methods
   - Appropriate mocking
   - Clear assertions
   - Comments explaining complex test scenarios

## Example Naming Convention
```java
@Test
@DisplayName("Should transition to COMPLETED state when all items processed successfully")
void shouldTransitionToCompletedWhenAllItemsProcessed() { ... }

@Test
@DisplayName("Should throw IllegalStateException when transition attempted from CANCELLED state")
void shouldThrowExceptionWhenTransitionFromCancelledState() { ... }
```

Please start with Step 1 - analyze the FSM and present it for my review.
