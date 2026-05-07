# HydrAIDE Claude Code Plugin

This repository is the [Claude Code](https://claude.com/claude-code) plugin for [HydrAIDE](https://github.com/hydraide/hydraide). It is generated from the HydrAIDE monorepo and **should not be edited directly** (see [Editing](#editing)).

## What you get

Three skills, automatically activated when relevant to your conversation:

| Skill | When it activates |
|---|---|
| **`hydraide`** | Conceptual / "how does X work" questions: Swamp lifecycle, addressing, query engine, msgpack patch, storage internals |
| **`hydraidego`** | Building Go applications: Profile/Catalog modelling, struct tags, server-side filters, locks, subscriptions, patches |
| **`hydraidectl`** | Operating HydrAIDE servers: install, upgrade, backup/restore, V1→V2 migration, observe, debug |

Slash commands (coming soon):

- `/hydraide-new-model`: interactive Profile/Catalog model generator with `RegisterPattern` boilerplate and a test scaffold
- `/hydraide-review`: structured code review against the HydrAIDE pitfall checklist
- `/hydraide-debug`: guided diagnostic flow (clock skew, register pattern, logs, `hydraidectl observe`)

## Install

```
/plugin marketplace add hydraide/claude
/plugin install hydraide
```

After install, Claude Code activates the relevant skill automatically when you ask a HydrAIDE-related question. There is no manual `Skill` invocation needed.

To enable automatic updates (recommended for this plugin):

```
/plugin
```

Then in the **Marketplaces** tab, toggle auto-update for `hydraide`. Otherwise, run `/plugin marketplace update hydraide` manually when you want the latest.

## What this plugin is not

- **Not a copy of HydrAIDE.** It contains skills (instructions for Claude) and a small set of concept docs. Source code, server, SDK, and full documentation remain in [`hydraide/hydraide`](https://github.com/hydraide/hydraide).
- **Not a runtime dependency.** Removing the plugin does not affect any HydrAIDE instance you operate.

## Editing

This repository is a **mirror**, not a source of truth. Skills and concept docs live in the HydrAIDE monorepo:

- Skills: [`hydraide/hydraide/.claude/skills/`](https://github.com/hydraide/hydraide/tree/main/.claude/skills)
- Concept docs: [`hydraide/hydraide/docs/features/`](https://github.com/hydraide/hydraide/tree/main/docs/features)

A GitHub Action in the HydrAIDE monorepo syncs them into this repo whenever they change. Direct commits to `main` here are blocked by branch protection.

If you want to suggest a change, open a PR against [`hydraide/hydraide`](https://github.com/hydraide/hydraide), and the change will land here automatically on merge.

## License

Apache 2.0, same as HydrAIDE itself.
