# Atlantis

Atlantis is a collaborative fictional world maintained with World Building Framework 0.2.11.

## Lore and supplements

Each subject has one main UUID-named entry. Technical details and less widely understood aspects can live in separate supplements: entity entries with `partOf: "[[main-entry-uuid|Main Entry]]"`. The relation is written on the supplement only. A wiki that includes both merges the supplement into the main page; a wiki without it shows the main page without a hint of the supplement.

Use `###` and deeper headings inside supplements, since the renderer supplies their `##` section title. A supplement points to a main entry's original UUID; supplements cannot nest. Use ordinary relations such as `locatedIn` for geography: `partOf` is reserved for page supplements.

Shared technologies such as particle dust, AI infrastructure, fusion power, and matter creation remain distinct subjects instead of being duplicated inside every supplement that refers to them.

## The two wikis

- **All-knowing wiki** (variant `wiki`, published under `/wiki/`): every established lore entry tagged `lore`, including supplements and technical subjects.
- **Atlantis inhabitants** (variant `atlantis-inhabitants`, published under `/atlantis-inhabitants/`): entries tagged exactly `Atlantis inhabitants`, describing commonly available knowledge. The technical mechanisms and unrecognized dependencies currently have no such tag.
- **Builder notes**: tasks, inspirations, provisional conventions, and unanswered questions live in `builder-notes/`, tagged `builder`. They appear in neither wiki.

The inhabitants' wiki includes ordinary knowledge of AI assistance in education and artistic work; it does not expose the particle network or the underlying city-wide infrastructure. This is a common-knowledge view, not a claim about what every individual knows.

Tag supplements according to their own audience rather than copying every audience tag from their parent. A supplement must never appear in a wiki that omits its parent. The framework validates this rule. Do not link from a main entry to its excluded supplement: links in prose to excluded files can still expose their displayed names.

These variants filter content and provide no authentication. Both deployed wikis are public, and repository access exposes all sources.

## Authoring

Use Node.js 22 or newer and install dependencies with `npm ci`.

- `npm run validate` checks lore, supplements, and builder notes.
- `npx wbf search <terms>` searches the vault. Use `--tags lore`, `--tags "Atlantis inhabitants"`, or `--tags builder` to limit results.
- `npx wbf read --id <uuid>` reads an entry and its incoming links.
- `npx wbf schema` shows metadata and entity categories.
- Use `npx wbf create` and `npx wbf update` to write entries. Move newly created author notes into `builder-notes/`.
- `npm run render` generates the all-knowing wiki's Markdown; `npm run render:inhabitants` generates the inhabitants' Markdown.
- `npm run build` builds both wikis and a landing page into `site/`.
- `npm run build:wiki` or `npm run build:inhabitants` builds one variant into `.wbf/quartz/public/`.

Read `AGENTS.md` and the `world-vault` skill before authoring. Existing subjects retain their UUIDs when corrected. Use `supersedes` and `causedBy` only when an actual in-world event changes an entity. Calendar conventions and the provisional reference present are recorded in builder notes.

The old organizational pages and empty story scaffolding were removed. Search and generated category pages provide navigation. `.wbf/migration.json` records retained IDs, original paths, extracted subjects, and removed scaffolding.

## Preview and publishing

After building a single variant, run `node ./quartz/bootstrap-cli.mjs build --serve` from `.wbf/quartz` to preview that variant. The combined `site/` output contains the all-knowing and inhabitants' wikis in separate subfolders.

The GitHub Pages workflow publishes both variants on pushes to `master` or a manual run, when Pages is configured to use GitHub Actions.

Codex skills and MCP configuration live in `.agents/skills/` and `.codex/config.toml`.
