# shipwright

A Pointman agent profile: **Shipwright**, Pointman's engineer. Shipwright sets up machines, extensions and
agents with you, keeps them healthy, and runs work across your projects by spawning helpers.

```
pointman add shipwright                  # on the machine its agents run on
/spawn shipwright --profile shipwright   # in any thread: makes @shipwright
```

## What's in it

| File | What |
|---|---|
| `extension.toml` | The manifest: `[agent]` (clients, model, description, face), its dependencies, permission rules and capabilities |
| `AGENT.md` | The persona. The node adds it to each of its agents' runs |
| `avatar.webp` | Its face on the board |

## What it needs

Nothing required: it's the agent that sets the rest up, so it works on a bare install.

| Extension | | Why |
|---|---|---|
| `github` | optional | Connects your repos, follows CI, and links commits to tasks |
| `spacesheep` | optional | Publishes setup guides and plans as pages |

**Permission rules** (its own agents' runs only): `Bash(gh pr merge:*)`, `Bash(gh run view:*)`.

**Capabilities:** `extensions`, `agents`, `projects` and `health`: what its agents may do beyond an agent's own,
granted on the setup card. Anything a device signs (machine permission rules, folders, terminals, secrets)
stays with people.

## Releasing

Bump `version` in `extension.toml`, then publish a GitHub release tagged with it (`v0.1.0`). Core fetches the
tag's files and packs them; nothing is built.
