---
description: "Start Chief Wiggum loop in current session"
argument-hint: "PROMPT [--max-iterations N] [--completion-promise TEXT]"
allowed-tools: ["Bash"]
hide-from-slash-command-tool: "true"
---

# Chief Loop Command

Run this command to initialize the Chief loop:

```bash
"${CLAUDE_PLUGIN_ROOT}/scripts/setup-chief-loop.sh" $ARGUMENTS
```

Execute the above command using Bash, then work on the task. When you try to exit, the Chief loop will feed the SAME PROMPT back to you for the next iteration. You'll see your previous work in files and git history, allowing you to iterate and improve.

CRITICAL RULE: If a completion promise is set, you may ONLY output it when the statement is completely and unequivocally TRUE. Do not output false promises to escape the loop, even if you think you're stuck or should exit for other reasons. The loop is designed to continue until genuine completion.

FORMAT REQUIREMENT: To signal completion, wrap the promise in `<promise>` tags. For example, if the completion promise is "DONE", output:
```
<promise>DONE</promise>
```
The text inside the tags must match the completion promise exactly.
