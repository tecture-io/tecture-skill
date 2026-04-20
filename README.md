# tecture — Claude Code skill

Author and maintain a file-based architecture at `./architecture/` — `manifest.json`, one JSON file per diagram, and one markdown description per node. Includes JSON schemas and a self-contained Node validator.

## Install

```bash
git clone https://github.com/tecture-io/tecture-skill.git ~/.claude/skills/tecture
```

Restart Claude Code. The skill activates when you ask Claude to create, update, split, or document an architecture as local JSON/Markdown files.

## Run the validator

From your project root (where `./architecture/` lives):

```bash
node ~/.claude/skills/tecture/scripts/validate.mjs
```

Exit codes: `0` success, `1` validation failure, `2` internal error. Pass a path to validate somewhere other than `./architecture`.

## What it does

- C4 levels 1–3 with cross-diagram drill-down via `subDiagramId` (slug-based, no UUIDs).
- Mermaid blocks inside per-node markdown for runtime / sequence detail.
- JSON Schema (Draft 2020-12) validation: shape, reference integrity, cycle detection, global node-id uniqueness, orphan-description warnings.
- No runtime dependencies.

See [`SKILL.md`](SKILL.md) for the full guide, [`reference/schema.md`](reference/schema.md) for the schema, and [`reference/example/`](reference/example/) for a minimal working architecture.

## Source of truth

This repo mirrors [tecture-io/tecture](https://github.com/tecture-io/tecture) at `.claude/skills/tecture/`. Open issues and PRs against the main repo.

## License

MIT — see [LICENSE](LICENSE).
