---
description: "Cancel active Chief Wiggum loop"
allowed-tools: ["Bash", "Read"]
hide-from-slash-command-tool: "true"
---

# Cancel Chief

To cancel the Chief loop:

1. Check if `.claude/chief-loop.local.md` exists using Bash: `test -f .claude/chief-loop.local.md && echo "EXISTS" || echo "NOT_FOUND"`

2. **If NOT_FOUND**: Say "No active Chief loop found."

3. **If EXISTS**:
   - Read `.claude/chief-loop.local.md` to get the current iteration number from the `iteration:` field
   - Remove the file using Bash: `rm .claude/chief-loop.local.md`
   - Report: "Cancelled Chief loop (was at iteration N)" where N is the iteration value
