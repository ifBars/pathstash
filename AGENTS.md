# PathStash agent guide

## Repository rules

- Use `bun` for JavaScript and TypeScript package management.
- Do not set or change `CARGO_TARGET_DIR`; use Cargo's default `target/` directory.
- Keep public repo content professional and product-facing. Do not commit scratch plans, private research notes, local tokens, or internal deployment notes.
- Generated UI concept images are references for implementation, not public site assets unless the user explicitly asks to publish them.

## UI and React work

Repo-local UI skills are installed under `.agents/skills`, with source hashes in `skills-lock.json`.

For a serious UI pass, start with:

- `.agents/skills/redesign-existing-projects/SKILL.md`
- `.agents/skills/design-taste-frontend/SKILL.md`
- `.agents/skills/high-end-visual-design/SKILL.md`
- `.agents/skills/image-taste-frontend/SKILL.md`
- `.agents/skills/stitch-design-taste/SKILL.md`
- `.agents/skills/shadcn/SKILL.md`

Use the narrower page/component skills when the task is scoped to a hero, CTA, card, grid, footer, branding, image optimization, or page-specific work.

## Current app surfaces

- `apps/web`: Vite React marketing site and dashboard shell, deployed as a Cloudflare Worker with static assets.
- `apps/relay`: Cloudflare Worker relay for account signup, tokens, devices, workspace manifests, encrypted secrets, blob storage, and markdown-for-agents responses.
- `apps/cli`: Rust CLI published as the `pathstash` crate.
- `packages/npm-cli`: TypeScript CLI package.
- `packages/mcp`: MCP server for agent clients.
