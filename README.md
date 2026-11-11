# skills 🦆

A small pack of agent skills, published as the **caalle** plugin for **Claude Code** and **Cursor**.

## Skills

| Skill | What it does | Use it when |
|---|---|---|
| [`story-gaps`](skills/story-gaps/SKILL.md) | Finds the open product decisions in a requirement before anyone writes the user story. It sorts the input into confirmed, assumed and unknown, keeps a decision record, and turns gaps into prioritised stakeholder questions. See the [worked example](skills/story-gaps/references/example.md). | You're writing, refining or reviewing a user story, epic or requirement, or preparing for refinement or Three Amigos. |
| [`unicornify-artifact`](skills/unicornify-artifact/SKILL.md) | Restyles an existing HTML page, report or dashboard in a light pastel rainbow-and-unicorn theme without changing its content or structure. Ships with a [reference stylesheet](skills/unicornify-artifact/references/theme.css) and an [example page](skills/unicornify-artifact/references/example.html). | You want a page or artifact in the rainbow / unicorn / pastel style. |

The agent picks a skill on its own when your request matches its description. You can also call one by name, see below.

Trying `story-gaps` for the first time? Pilot it on one requirement. Note which questions helped, which were noise, and how long the review took, then decide whether to make it the default for refinement.

## Install

### Claude Code

Inside Claude Code:

```
/plugin marketplace add caalle/skills
```

```
/plugin install caalle@caalle
```

Or from your shell:

```bash
claude plugin marketplace add caalle/skills
```

```bash
claude plugin install caalle@caalle
```

Plugin skills are namespaced, so you call them as `/caalle:story-gaps` and `/caalle:unicornify-artifact`.

To get new versions, run `/plugin marketplace update caalle`, or turn on auto-update for the marketplace in `/plugin`.

### Cursor

The repository root is a Cursor plugin (`.cursor-plugin/plugin.json`).

- **Team:** in the Cursor dashboard, open **Plugins & MCPs**, choose **Add Marketplace → Import from Repo**, and enter `https://github.com/caalle/skills`. Then install **caalle**.
- **Personal:** add the repository from the plugins area of the Cursor app, then install **caalle**.

See [Cursor's plugin docs](https://cursor.com/docs/plugins) for the current steps.

### Without the plugin

Each skill is a plain folder with a `SKILL.md`, so you can also copy a folder from `skills/` into your tool's skills directory, for example `~/.claude/skills/` for Claude Code.

## Repository layout

```
.claude-plugin/marketplace.json     Claude Code marketplace ("caalle"), with the repo root as its one plugin
.claude-plugin/plugin.json          Claude Code plugin manifest ("caalle")
.cursor-plugin/plugin.json          Cursor plugin manifest ("caalle")
.github/workflows/validate.yml      CI: manifest validation, version and skill checks
skills/
  story-gaps/SKILL.md
  story-gaps/references/example.md
  unicornify-artifact/SKILL.md
  unicornify-artifact/references/theme.css
  unicornify-artifact/references/example.html
```

The whole repository is one plugin, so every skill in `skills/` ships in it.

## Adding a skill

1. Create `skills/<skill-name>/SKILL.md` with `name` and `description` frontmatter. `name` must equal the folder name. Both Claude Code and Cursor pick up new skill folders automatically.
2. Keep `SKILL.md` short: rules, workflow, and what good output looks like. Put long material (stylesheets, worked examples, templates) in `references/` and link to it.
3. Add a row to the Skills table above.
4. Bump `version` in **both** `plugin.json` files. Installed copies only update when the version changes. CI fails if the two versions differ.
5. Run the same checks as CI:

   ```bash
   claude plugin validate .
   ```

## License

[MIT](LICENSE)
