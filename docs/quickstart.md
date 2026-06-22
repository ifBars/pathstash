# Quickstart

PathStash has two pieces:

- a Rust CLI that scans and hydrates a code root
- a Cloudflare relay that stores workspace metadata, manifests, and content-addressed blobs

## Install the CLI

```powershell
cargo install pathstash --locked
```

## Initialize a workspace

```powershell
pathstash init --root C:\Code --name "Desktop"
```

This creates:

- `.pathstash/config.json`
- `.pathstashignore`

PathStash also reads legacy `.devdrop/` and `.devdropignore` files so existing users do not lose state during the rename.

## Push a workspace

Sign in once, then push:

```powershell
pathstash login
pathstash push --root C:\Code
```

`pathstash login` stores the relay token in the operating system credential store. `--token`, `PATHSTASH_TOKEN`, and the legacy `DEVDROP_TOKEN` still work for CI and temporary sessions.

`push` sends the manifest and uploads file blobs up to 1 MiB. Larger files still appear in the manifest, but their contents are not uploaded by default.

## Hydrate on another machine

Use the workspace id printed by `push`:

```powershell
pathstash hydrate --root C:\Code-Restored --workspace-id "<workspace-id>"
```

Hydration creates directories first, then downloads available blobs. Existing files are left alone unless you pass `--force`.

For a structure-only restore:

```powershell
pathstash hydrate --root C:\Code-Restored --workspace-id "<workspace-id>" --directories-only
```

## Check the hosted relay

```powershell
Invoke-RestMethod https://devdrop-relay.ifbars.workers.dev/health
```

The health endpoint does not require authentication.

The hosted relay URL is still the default while the service moves to the PathStash name:

```text
https://devdrop-relay.ifbars.workers.dev
```

Pass `--relay` only when using a different relay.

## What gets skipped

The default ignore set skips generated and private local state:

- `.git/`
- `.pathstash/`
- `.devdrop/`
- `node_modules/`
- `target/`
- `dist/`
- `.next/`
- `.wrangler/`
- `internal/`
- `infra/live-test-token.txt`
- `bin/`
- `obj/`
- `Library/`
