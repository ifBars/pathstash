# Deployment

## Cloudflare resources

The current hosted relay still uses the original Devdrop resource names while the public project moves to PathStash:

- Worker: `devdrop-relay`
- D1 database: `devdrop-meta`
- R2 bucket: `devdrop-objects`
- Queue: `devdrop-events`
- Durable Object: `WorkspaceSession`

## Commands

```powershell
cd apps\relay
bun install
bun run cf:types
bunx wrangler secret put DEV_AUTH_TOKEN
bunx wrangler deploy --minify
```

The checked-in `wrangler.jsonc` points at the current D1 database, R2 bucket, Queue, and Durable Object binding. To deploy your own relay, create those resources first, then update the ids in `wrangler.jsonc`.

Keep local tokens and deployment scratch notes out of Git.
