# quackpack 🦆

A small pack of agent skills, packaged as a plugin for **Claude Code** and **Cursor**.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| [`gap-analysis`](plugins/quackpack/skills/gap-analysis/SKILL.md) | Finds the open product decisions in a requirement before anyone writes the user story. It sorts the input into confirmed, assumed and unknown, keeps a decision record, and turns gaps into prioritised stakeholder questions. | You're writing, refining or reviewing a user story, epic or requirement, or preparing for refinement or Three Amigos. |
| [`rainbow-unicorn-theme`](plugins/quackpack/skills/rainbow-unicorn-theme/SKILL.md) | Restyles an existing HTML artifact in a light pastel rainbow-and-unicorn theme without changing its content or structure. Ships with a [reference stylesheet](plugins/quackpack/skills/rainbow-unicorn-theme/references/theme.css). | You want an artifact, report or dashboard in the rainbow / unicorn / pastel style. |

The agent picks a skill on its own when your request matches its description. You can also call one by name (see below).

## Install

### Claude Code

Inside Claude Code:

```
/plugin marketplace add caalle/quackpack
```

```
/plugin install quackpack@quackpack
```

Or from your shell:

```bash
claude plugin marketplace add caalle/quackpack
```

```bash
claude plugin install quackpack@quackpack
```

Plugin skills are namespaced, so you call them as `/quackpack:gap-analysis` and `/quackpack:rainbow-unicorn-theme`.

To get new versions, run `/plugin marketplace update quackpack`, or turn on auto-update for the marketplace in `/plugin`.

### Cursor

This repo is a Cursor plugin marketplace (`.cursor-plugin/marketplace.json`).

- **Team marketplace:** in the Cursor dashboard, open **Plugins & MCPs**, choose **Add Marketplace → Import from Repo**, and enter `https://github.com/caalle/quackpack`. Then install **quackpack** from the marketplace.
- **Personal:** add the repository as a marketplace from the plugins area of the Cursor app, then install **quackpack**.

See [Cursor's plugin docs](https://cursor.com/docs/plugins) for the current steps.

### Without the plugin

Each skill is a plain folder with a `SKILL.md`, so you can also copy a folder from `plugins/quackpack/skills/` into your tool's skills directory, for example `~/.claude/skills/` for Claude Code.

## Repository layout

```
.claude-plugin/marketplace.json     Claude Code marketplace
.cursor-plugin/marketplace.json     Cursor marketplace
plugins/quackpack/
  .claude-plugin/plugin.json        Claude Code plugin manifest
  .cursor-plugin/plugin.json        Cursor plugin manifest
  skills/
    gap-analysis/SKILL.md
    rainbow-unicorn-theme/SKILL.md
    rainbow-unicorn-theme/references/theme.css
```

## Adding a skill

1. Create `plugins/quackpack/skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter. Both Claude Code and Cursor pick up new skill folders automatically.
2. Add a row to the Skills table above.
3. Bump `version` in **both** `plugin.json` files. Installed copies only update when the version changes.
4. Check the Claude manifests:

   ```bash
   claude plugin validate .
   ```

## License

[MIT](LICENSE)
