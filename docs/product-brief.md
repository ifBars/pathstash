# Product brief

PathStash is for developers who work from more than one machine and are tired of rebuilding their workspace by memory.

Git is still the source of truth for code history. PathStash handles the layer around Git: where repositories live, which generated folders should be ignored, what a machine needs to know before an agent starts working, and how to move that workspace map from one box to another.

The first useful version should answer a simple question:

> Can I point a new machine or agent at my code root and have it understand the shape of my workspace immediately?

## First users

- Developers with a laptop, desktop, build box, and cloud agent runner.
- People who maintain many small repos and keep losing track of local paths.
- Teams that want repeatable onboarding without forcing every repo into a meta-repo.

## First product loop

1. Run `pathstash init` in a code root.
2. Let PathStash scan the tree while skipping generated folders.
3. Push the manifest and small file blobs to a hosted relay.
4. Hydrate the workspace on another machine without overwriting local work.

The product gets more interesting once encrypted local state, device grants, and agent handoff packets are layered on top. The first version stays focused on the sync spine: capture the workspace, move it, and restore it safely.
