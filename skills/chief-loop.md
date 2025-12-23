---
description: "Start self-referential development loop for iterative tasks. Use when user asks to 'chief wiggum', 'wiggum it', 'run in a loop until done', or wants iterative development with automatic self-correction."
---

# Chief Wiggum Loop

The user wants to run a task in a self-referential loop where you iterate until completion.

## When to use this

- User says "chief wiggum this", "wiggum it", "ralph it"
- User wants you to "keep trying until it works"
- User asks for iterative development with self-correction
- User wants to "run in a loop" until a task is complete
- User mentions wanting automatic retry/iteration behavior

## How to start the loop

Run the `/chief-loop` command with the user's task:

```
/chief-loop "<TASK DESCRIPTION>" --completion-promise "<SUCCESS_CRITERIA>" --max-iterations <N>
```

### Constructing the command

1. **Task description**: Convert the user's request into a clear task prompt
2. **Completion promise**: Define what "done" means - a true statement when complete
3. **Max iterations**: Default to 20-50 for safety, adjust based on task complexity

### Examples

User: "Chief wiggum adding tests until they all pass"
```
/chief-loop "Add comprehensive tests for the authentication module. Run tests after each change." --completion-promise "All tests passing" --max-iterations 30
```

User: "Wiggum it - fix the build errors"
```
/chief-loop "Fix all build errors. Run the build after each fix attempt." --completion-promise "Build successful" --max-iterations 20
```

User: "Keep trying to implement this feature until it works"
```
/chief-loop "Implement the user dashboard feature with charts and data tables. Test manually after each iteration." --completion-promise "Feature complete and working" --max-iterations 40
```

## Important notes

- Always set `--max-iterations` as a safety net
- The completion promise must be something that becomes TRUE when done
- You will see your previous work in files between iterations
- The loop continues automatically - you don't need to restart it
