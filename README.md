# Atlantis

Atlantis is a collaborative fictional world maintained with World Building Framework 0.2.9.

## Content

The repository root holds 22 UUID-named lore entries. Titles and categories live in frontmatter; relationships use `[[uuid|Title]]` links in the text and in named frontmatter fields. Existing subjects retain their UUIDs when reorganized. Structural corrections do not represent fictional historical changes.

Entity categories are `location`, `society`, `institution`, `technology`, `creature`, `role`, `tradition`, and `note`. A recurring tradition such as the Festival is distinct from a specific occurrence recorded as an event. No dated events were invented during restructuring.

`builder-notes/` holds four linked collections of questions and working ideas, plus the world's inspirations. These five author notes are tagged `builder`, remain searchable through the framework, and are excluded from the wiki. Provisional details and unanswered questions belong there. Their links to lore entries also appear under `linkedFrom` when reading those entries.

Obsolete organizational pages and empty story scaffolding have been removed. Search and the generated wiki's category pages provide navigation. `.wbf/migration.json` records retained UUIDs, extracted subjects, original source paths, and removed scaffolding.

## Working with the world

Use Node.js 22 or newer and install pinned dependencies with `npm ci`.

- `npm run validate` checks lore and builder notes, including their links.
- `npx wbf search <terms>` searches titles, aliases, and text. Add `--tags public` or `--tags builder` to limit the audience.
- `npx wbf read --id <uuid>` reads an entry and its incoming links.
- `npx wbf schema` shows metadata and entity categories.
- Use `npx wbf create` and `npx wbf update` to write entries. Move newly created author notes to `builder-notes/`.
- `npm run render` generates wiki Markdown locally.
- `npm run build` builds the wiki, downloading the pinned Quartz renderer on first use.

Read `AGENTS.md` and the installed `world-vault` skill before authoring. Use `supersedes` and `causedBy` only when an actual in-world event changes an entity.

## Audiences and publishing

The `wiki` variant includes only entries tagged `public`. Author notes carry `builder` instead. World truths unknown to inhabitants belong in separate entries tagged `non-public`; do not mix them into public entries or apply both audience tags. Variants filter whole files and provide no authentication. Repository access exposes all source files; every deployed variant is public.

After `npm run build`, run `node ./quartz/bootstrap-cli.mjs build --serve` from `.wbf/quartz` for a local preview.

The GitHub Pages workflow runs on pushes to `main` and manual runs. Deployment requires **Settings → Pages → Source: GitHub Actions** in the existing repository. Setup and restructuring did not publish or change the remote repository.

Codex skills and MCP configuration are installed in `.agents/skills/` and `.codex/config.toml`.
