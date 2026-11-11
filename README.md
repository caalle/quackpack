# skills 🦆

A small pack of agent skills, published as the **quackpack** plugin for **Claude Code** and **Cursor**.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| [`story-gaps`](plugins/quackpack/skills/story-gaps/SKILL.md) | Finds the open product decisions in a requirement before anyone writes the user story. It sorts the input into confirmed, assumed and unknown, keeps a decision record, and turns gaps into prioritised stakeholder questions. See the [worked example](plugins/quackpack/skills/story-gaps/references/example.md). | You're writing, refining or reviewing a user story, epic or requirement, or preparing for refinement or Three Amigos. |
| [`unicornify-artifact`](plugins/quackpack/skills/unicornify-artifact/SKILL.md) | Restyles an existing HTML page, report or dashboard in a light pastel rainbow-and-unicorn theme without changing its content or structure. Ships with a [reference stylesheet](plugins/quackpack/skills/unicornify-artifact/references/theme.css) and an [example page](plugins/quackpack/skills/unicornify-artifact/references/example.html). | You want a page or artifact in the rainbow / unicorn / pastel style. |

The agent picks a skill on its own when your request matches its description. You can also call one by name, see below.

Trying `story-gaps` for the first time? Pilot it on one requirement. Note which questions helped, which were noise, and how long the review took, then decide whether to make it the default for refinement.

## Install

### Claude Code

Inside Claude Code:

```
/plugin marketplace add caalle/skills
```

```
/plugin install quackpack@caalle
```

Or from your shell:

```bash
claude plugin marketplace add caalle/skills
```

```bash
claude plugin install quackpack@caalle
```

Plugin skills are namespaced, so you call them as `/quackpack:story-gaps` and `/quackpack:unicornify-artifact`.

To get new versions, run `/plugin marketplace update caalle`, or turn on auto-update for the marketplace in `/plugin`.

### Cursor

This repo is a Cursor plugin marketplace (`.cursor-plugin/marketplace.json`).

- **Team marketplace:** in the Cursor dashboard, open **Plugins & MCPs**, choose **Add Marketplace → Import from Repo**, and enter `https://github.com/caalle/skills`. Then install **quackpack** from the marketplace.
- **Personal:** add the repository as a marketplace from the plugins area of the Cursor app, then install **quackpack**.

See [Cursor's plugin docs](https://cursor.com/docs/plugins) for the current steps.

### Without the plugin

Each skill is a plain folder with a `SKILL.md`, so you can also copy a folder from `plugins/quackpack/skills/` into your tool's skills directory, for example `~/.claude/skills/` for Claude Code.

## Repository layout

```
.claude-plugin/marketplace.json     Claude Code marketplace ("caalle")
.cursor-plugin/marketplace.json     Cursor marketplace ("caalle")
.github/workflows/validate.yml      CI: manifest validation, version and skill checks
plugins/quackpack/
  .claude-plugin/plugin.json        Claude Code plugin manifest
  .cursor-plugin/plugin.json        Cursor plugin manifest
  skills/
    story-gaps/SKILL.md
    story-gaps/references/example.md
    unicornify-artifact/SKILL.md
    unicornify-artifact/references/theme.css
    unicornify-artifact/references/example.html
```

The marketplace is named after the owner so more plugins can be added next to `quackpack` later.

## Adding a skill

1. Create `plugins/quackpack/skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter. `name` must equal the folder name. Both Claude Code and Cursor pick up new skill folders automatically.
2. Keep `SKILL.md` short: rules, workflow, and what good output looks like. Put long material (stylesheets, worked examples, templates) in `references/` and link to it.
3. Add a row to the Skills table above.
4. Bump `version` in **both** `plugin.json` files. Installed copies only update when the version changes. CI fails if the two versions differ.
5. Run the same checks as CI:

   ```bash
   claude plugin validate .
   claude plugin validate plugins/quackpack
   ```

## License

[MIT](LICENSE)
