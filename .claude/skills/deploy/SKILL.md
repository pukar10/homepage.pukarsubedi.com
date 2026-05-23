---
name: deploy
description: Build the Next.js site and deploy it to the self-hosted VPS via SSH/rsync. Use when the user wants to push changes to production.
disable-model-invocation: true
---

# Deploy to VPS

Run a production build and transfer the output to the self-hosted VPS.

## Steps

1. Run `npm run build` and confirm it succeeds with no errors.
2. Confirm the user wants to push to production before proceeding.
3. Use `rsync` or `scp` to copy the build output (`.next/` and `public/`) to the VPS.
4. SSH into the VPS and restart the Node.js process (e.g., `pm2 restart homepage` or `systemctl restart homepage`).
5. Report success or any errors.

## Notes

- Ask the user for their VPS host, deploy path, and process manager if not already known. Save them in CLAUDE.local.md for future runs.
- This skill does NOT assume Vercel or any managed platform — all steps are manual SSH/rsync.
- If $ARGUMENTS are provided, treat them as the deploy target (e.g., `staging` vs `production`).
