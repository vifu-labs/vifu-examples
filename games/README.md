# Games

Each entry identifies the original open-source project and shows how it becomes
a Vifu-native game without obscuring its authorship or upstream history.

## [AIventure](aiventure)

- **Original project:** [bebechien/AIventure](https://github.com/bebechien/AIventure)
- **Vifu integration:** Vifu publishing and runtime support, with `@vifu/hub`
  as the game-to-platform interface for AI, tools, state, resources, and other
  host-managed capabilities.

AIventure is included as a Git submodule so its source and Vifu integration
remain visible together.

If the folder is empty after cloning:

```bash
git submodule update --init --recursive
```

## [AI Town](ai-town)

- **Original project:** [a16z-infra/ai-town](https://github.com/a16z-infra/ai-town)
- **Vifu integration:** Vifu build configuration and runtime adapters connect
  the town simulation's Convex-style state and world sessions to the Vifu game
  runtime.

AI Town is a virtual town where AI characters live, chat, and socialize. Its
source remains a Git submodule so the upstream project and Vifu integration
history stay inspectable together.

## [Agentshire](agentshire)

- **Original project:** [vifudotdev/Agentshire](https://github.com/vifudotdev/Agentshire)
- **Runtime model:** An OpenClaw/QClaw plugin that maps agents to social NPCs
  in a browser-based 3D town, with a WebSocket event bridge, town editor, and
  character workshop.

Agentshire remains a Git submodule so its plugin, bridge, and 3D town frontend
can evolve with their own source history.

## [Microverse](microverse)

- **Original project:** [KsanaDock/Microverse](https://github.com/KsanaDock/Microverse)
- **Runtime model:** A Godot 4 multi-agent social sandbox where autonomous
  characters talk, form memories, plan tasks, and move through a shared
  workplace.

The Vifu-maintained fork remains a Git submodule so the Godot project and its
integration work retain their own source history.
