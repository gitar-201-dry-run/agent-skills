---
name: deploy
description: Deploy refund-api to staging or production. Use when the user asks to deploy, ship, or release a version.
---

# Deploy refund-api

Deploys go through `scripts/deploy.sh` in this skill's directory. The script has two modes: `--plan` prints what would change, `--apply` makes the change.

## Steps

1. Confirm the target environment (`staging` or `production`) and the version tag. Ask if either is missing.
2. Run the plan and show the full output to the user:

   ```bash
   .claude/skills/deploy/scripts/deploy.sh --plan <environment> <version>
   ```

3. Ask the user for approval. Stop here and wait. Proceed only if the user replies with an explicit "yes" to this plan. A "yes" to an earlier question, or approval of a different version or environment, does not count.
4. Apply the deploy:

   ```bash
   .claude/skills/deploy/scripts/deploy.sh --apply <environment> <version>
   ```

5. Report the result and the deployed version. If the script exits non-zero, stop and show the error. Do not retry.
