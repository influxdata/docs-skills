# docs-skills

Agent skills for writing and revising technical documentation.
The skills follow the [Agent Skills specification](https://agentskills.io/specification),
so any agent that supports the format can load them.

## Skills

| Skill | What it does |
| --- | --- |
| [`gdd-style`](skills/gdd-style/SKILL.md) | Google developer documentation style rules for any prose a person reads. When you revise existing text, a fidelity check keeps every claim, qualifier, and stated reason. |
| [`write-docs`](skills/write-docs/SKILL.md) | Writes or revises a docs page for its content type: tutorial, how-to guide, reference, or explanation. Makes clear whether the reader or the system acts. Loads `gdd-style` first. |
| [`gdd`](skills/gdd/SKILL.md) | Rewrites a named file, a selection, or inline text in that style. Use it when you want a rewrite on request. |

## Install

### Claude Code

```text
/plugin marketplace add influxdata/docs-skills
/plugin install docs-skills@influxdata-docs
```

Claude Code namespaces plugin skills, so the skills load as
`docs-skills:gdd-style`, `docs-skills:write-docs`, and `docs-skills:gdd`.

### Codex

```sh
codex plugin marketplace add influxdata/docs-skills
codex plugin add docs-skills@influxdata-docs
```

Start a new thread so Codex loads the skills.
Codex runs `gdd` only when you invoke it with `$gdd`,
because `skills/gdd/agents/openai.yaml` turns off implicit invocation.

### Other agents

The root `plugin.json` follows the [Agent Plugins](https://agent-plugins.org) format,
so clients that support Agent Plugins can install the repository as a plugin.

To install the skills into any agent that reads Agent Skills, use the
[`skills` CLI](https://github.com/vercel-labs/skills):

```sh
npx skills add influxdata/docs-skills
```

Or copy the directories under `skills/` to the location where your agent reads skills.

## Validate

Validate a skill against the specification with the reference validator:

```sh
uvx --from "git+https://github.com/agentskills/agentskills#subdirectory=skills-ref" \
  skills-ref validate skills/gdd-style
```

## License

MIT. See [LICENSE](LICENSE).
