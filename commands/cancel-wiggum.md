---
description: "Cancel active Wiggum loop"
allowed-tools: ["Bash", "Read"]
hide-from-slash-command-tool: "true"
---

# Cancel Wiggum

To cancel the Wiggum loop:

1. Check if `.claude/wiggum-loop.local.md` exists using Bash: `test -f .claude/wiggum-loop.local.md && echo "EXISTS" || echo "NOT_FOUND"`

2. **If NOT_FOUND**: Say "No active Wiggum loop found."

3. **If EXISTS**:
   - Read `.claude/wiggum-loop.local.md` to get the current iteration number from the `iteration:` field
   - Remove the file using Bash: `rm .claude/wiggum-loop.local.md`
   - Report: "Cancelled Wiggum loop (was at iteration N)" where N is the iteration value
