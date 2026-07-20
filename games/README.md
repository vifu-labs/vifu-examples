# Games

Each entry identifies the original open-source project, its playable build, and
its upstream history.

## [AIventure](aiventure)

- **Original project:** [bebechien/AIventure](https://github.com/bebechien/AIventure)
- **Play:** [Open AIventure](https://vifu.ai/damon/AIventure)

AIventure is a multiplayer adventure game where players explore a persistent
world with AI-driven characters. Its source remains available as a Git
submodule.

If the folder is empty after cloning:

```bash
git submodule update --init --recursive
```

## [AI Town](ai-town)

- **Original project:** [a16z-infra/ai-town](https://github.com/a16z-infra/ai-town)
- **Play:** [Open AI Town](https://vifu.ai/damon/ai-town)

AI Town is a virtual town where AI characters live, chat, and socialize. Its
source remains a Git submodule so its upstream history stays inspectable.

## [AI Death Game](ai-death-game)

- **Original project:** [yami-inc/ai-death-game](https://github.com/yami-inc/ai-death-game)
- **Play:** [Open AI Death Game](https://vifu.ai/damon/ai-death-game)

AI Death Game is a narrative survival game where five AI characters debate,
betray, and vote while the player directs the game as its GM.

## [Agentshire](agentshire)

- **Original project:** [Agentshire/Agentshire](https://github.com/Agentshire/Agentshire)
- **Play:** [Open Agentshire](https://vifu.ai/damon/agentshire)
- **Runtime model:** An OpenClaw/QClaw plugin that maps agents to social NPCs
  in a browser-based 3D town, with a WebSocket event bridge, town editor, and
  character workshop.

Agentshire remains a Git submodule so its plugin, bridge, and 3D town frontend
can evolve with their own source history.

## [Microverse](microverse)

- **Original project:** [KsanaDock/Microverse](https://github.com/KsanaDock/Microverse)
- **Play:** [Open Microverse](https://vifu.ai/damon/microverse)
- **Runtime model:** A Godot 4 multi-agent social sandbox where autonomous
  characters talk, form memories, plan tasks, and move through a shared
  workplace.

The maintained fork remains a Git submodule so the Godot project retains its
own source history.
