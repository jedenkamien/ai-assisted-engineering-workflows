# AI-Assisted Testing

Techniques for adding and maintaining unit tests with minimal context and effort.

The focus is not on generating tests in general, but on supplying the LLM with the smallest amount of information required to produce useful results.

## Available Techniques

### Diff-Based Test Generation

Generate tests only for behavior introduced by a code change.

See:
- [Diff-Based](./unit-tests-scenarios.md#diff-based-test-generation)

### Implementation-Based Test Generation

Generate tests by analyzing an implementation class and deriving its main use cases.

See:
- [Implementation-Based](./unit-tests-scenarios.md#implementation-based-test-generation)

### Test Repair After Intentional Changes

Identify why a test became invalid after a deliberate production code change and adjust the test accordingly.

See:
- [Test Repair After Intentional Changes](./unit-tests-scenarios.md#test-repair-after-intentional-changes)

## Evolution into AI Skills

Although the examples in this folder are currently provided as prompts, each technique can be naturally evolved into an AI skill (for example GitHub Copilot custom instructions, prompt files, Copilot Studio agents, or IDE-integrated workflows).

The prompts already define:
- the required inputs,
- the expected outcome,
- and the reasoning strategy.

As a result, they can be turned into reusable, one-click developer tools with relatively little additional effort.
