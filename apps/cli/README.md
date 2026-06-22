# pathstash

`pathstash` is the command-line client for PathStash, a small workspace sync tool for developers who move between machines or agent environments.

It scans a code root, skips generated and private local state, pushes a manifest to a relay, uploads small content-addressed file blobs, and can hydrate that root somewhere else.

## Install

```powershell
cargo install pathstash --locked
```

## Basic flow

```powershell
pathstash init --root C:\Code --name "Workstation"
pathstash login
pathstash push --root C:\Code
pathstash hydrate --root C:\Code-Restored --workspace-id "<workspace-id>"
```

`pathstash login` stores the relay token in the operating system credential store. `PATHSTASH_TOKEN` and the legacy `DEVDROP_TOKEN` environment variable still work for CI and temporary sessions.

The hosted relay is still `https://devdrop-relay.ifbars.workers.dev` during the rename, and it is the default relay URL.
