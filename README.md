# Skills

Claude Code skills, published as a marketplace.

## Installing

```
/plugin marketplace add codomaniac/skills
/plugin install claude-proofread@codomaniac
```

`/plugin marketplace update` picks up anything added later.

## What is here

| Skill | What it does |
| --- | --- |
| `claude-proofread` | Reports on prose without editing it: mechanical errors with the rule behind each, words the author is talking around, and clutter by Zinsser's rules in *On Writing Well*. |
| `proofread` | The same proofreading, written out as the JSON report the [Obsidian Proofread plugin](https://github.com/codomaniac/obsidian-proofread) draws on a note. |

`proofread` is listed from the plugin's own repository rather than copied here,
because it is tied to that plugin's report format and the two have to change
together. `claude-proofread` is the one to install for proofreading in the
terminal, with no Obsidian involved.

## Layout

A marketplace lists plugins, not bare skills, so each skill kept here is wrapped
in a plugin directory:

```
.claude-plugin/marketplace.json   the catalog
plugins/<name>/
  .claude-plugin/plugin.json      name, version, author
  skills/<name>/SKILL.md          the skill itself
```

An entry in the catalog is either a directory here or a pointer somewhere else:

```json
{ "name": "claude-proofread", "source": "claude-proofread" }
{ "name": "proofread",
  "source": { "source": "github", "repo": "codomaniac/obsidian-proofread" } }
```

## Adding a skill

1. `plugins/<name>/skills/<name>/SKILL.md` — the skill, with its `name` and
   `description` front matter.
2. `plugins/<name>/.claude-plugin/plugin.json` — same name, a version, an author.
3. An entry in `.claude-plugin/marketplace.json`.
4. `claude plugin validate .` and `claude plugin validate plugins/<name>`.

Bump the version in `plugin.json` when a skill changes; that is what tells an
installed copy it is out of date.
