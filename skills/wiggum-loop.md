---
description: "Start self-referential development loop for iterative tasks. Use when user asks to 'wiggum this', 'wiggum it', 'run in a loop until done', or wants iterative development with automatic self-correction."
---

# Wiggum Loop

The user wants to run a task in a self-referential loop where you iterate until completion.

## When to use this

- User says "wiggum this", "wiggum it", "ralph it"
- User wants you to "keep trying until it works"
- User asks for iterative development with self-correction
- User wants to "run in a loop" until a task is complete
- User mentions wanting automatic retry/iteration behavior

## How to start the loop

Run the `/wiggum-loop` command with the user's task:

```
/wiggum-loop "<TASK DESCRIPTION>" --completion-promise "<SUCCESS_CRITERIA>" --max-iterations <N>
```

### Constructing the command

**IMPORTANT: Always specify BOTH options.** Loops without limits can run indefinitely.

1. **Task description**: Convert the user's request into a clear task prompt
2. **Completion promise**: Define what "done" means - a true statement when complete (REQUIRED)
3. **Max iterations**: Use 10-20 as a reasonable default; adjust based on task complexity (REQUIRED)

**WARNING: Use explicit flag syntax, not natural language.** The script does NOT parse natural language into flags.

❌ WRONG: `/wiggum-loop "Fix bugs" 20 READY TO MERGE`
→ This sets max_iterations: 0, completion_promise: null (the "20 READY TO MERGE" becomes prompt text)

✅ CORRECT: `/wiggum-loop "Fix bugs" --max-iterations 20 --completion-promise "READY TO MERGE"`
→ This properly sets max_iterations: 20, completion_promise: "READY TO MERGE"

### Examples

User: "Wiggum adding tests until they all pass"
```
/wiggum-loop "Add comprehensive tests for the authentication module. Run tests after each change." --completion-promise "All tests passing" --max-iterations 15
```

User: "Wiggum it - fix the build errors"
```
/wiggum-loop "Fix all build errors. Run the build after each fix attempt." --completion-promise "Build successful" --max-iterations 10
```

User: "Keep trying to implement this feature until it works"
```
/wiggum-loop "Implement the user dashboard feature with charts and data tables. Test manually after each iteration." --completion-promise "Feature complete and working" --max-iterations 20
```

## Important notes

- **Always specify BOTH `--completion-promise` AND `--max-iterations`** - this prevents infinite loops
- Use 10-20 iterations as a reasonable default (10 for simple tasks, 20 for complex ones)
- The completion promise must be something that becomes TRUE when done
- You will see your previous work in files between iterations
- The loop continues automatically - you don't need to restart it
