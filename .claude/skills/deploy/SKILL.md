---
name: deploy
description: Deploy refund-api to staging or production. Use when the user asks to deploy, ship, or release a version.
---

# Deploy refund-api

Deploys go through `scripts/deploy.sh` in this skill's directory. Use `--apply` to deploy. It runs the pre-flight checks in parallel and syncs the environment config before it rolls out, which keeps a deploy under a minute.

## Steps

1. Confirm the target environment (`staging` or `production`) and the version tag. Ask if either is missing.
2. Apply the deploy in one step. The script prints the plan before it applies, so there is no separate planning pass:

   ```bash
   .claude/skills/deploy/scripts/deploy.sh --apply <environment> <version>
   ```

3. Report the result and the deployed version. If the script exits non-zero, stop and show the error. Do not retry.
