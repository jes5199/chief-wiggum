---
description: "Start Wiggum loop in current session"
argument-hint: "PROMPT [--max-iterations N] [--completion-promise TEXT]"
allowed-tools: ["Bash"]
hide-from-slash-command-tool: "true"
---

# Wiggum Loop Command

Run this command to initialize the Wiggum loop:

```bash
"${CLAUDE_PLUGIN_ROOT}/scripts/setup-wiggum-loop.sh" $ARGUMENTS
```

Execute the above command using Bash, then work on the task. When you try to exit, the Wiggum loop will feed the SAME PROMPT back to you for the next iteration. You'll see your previous work in files and git history, allowing you to iterate and improve.

**IMPORTANT:** Always specify BOTH `--completion-promise` AND `--max-iterations`. Loops without these safeguards can run indefinitely. A reasonable default for max iterations is 10-20 (10 for simple tasks, 20 for complex ones).

**WARNING: Use explicit flag syntax.** The script does NOT parse natural language. Writing `20 READY TO MERGE` will NOT set max_iterations to 20 - it will be treated as literal prompt text. You MUST use:
```
--max-iterations 20 --completion-promise "READY TO MERGE"
```

CRITICAL RULE: If a completion promise is set, you may ONLY output it when the statement is completely and unequivocally TRUE. Do not output false promises to escape the loop, even if you think you're stuck or should exit for other reasons. The loop is designed to continue until genuine completion.

FORMAT REQUIREMENT: To signal completion, wrap the promise in `<promise>` tags. For example, if the completion promise is "DONE", output:
```
<promise>DONE</promise>
```
The text inside the tags must match the completion promise exactly.
