# Awesome Open Source AI Native Games

A curated collection of open-source AI-native games and Vifu starters. Every
game keeps its original GitHub project visible while its Vifu integration makes
it a first-class project in Vifu's publish and runtime environment.

## Get The Collection

Clone with submodules:

```bash
git clone --recurse-submodules https://github.com/vifudotdev/awesome-open-source-ai-native-games
cd awesome-open-source-ai-native-games
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

## Games

### [AIventure](games/aiventure)

- **Original project:** [bebechien/AIventure](https://github.com/bebechien/AIventure)
- **Vifu integration:** brings AIventure into Vifu's publish and runtime flow.
  `@vifu/hub` establishes its Vifu-native game surface for AI agents and tools,
  game state, resources, worlds, and approved runtime capabilities. AIventure
  uses it for model-driven NPC play without embedding provider credentials or
  host plumbing in the game.

The Vifu integration is a Git submodule, so its source and integration history
stay inspectable alongside the original project.

### [AI Town](games/ai-town)

- **Original project:** [a16z-infra/ai-town](https://github.com/a16z-infra/ai-town)
- **Vifu integration:** Vifu build configuration and runtime adapters connect
  the town simulation's Convex-style state and world sessions to the Vifu game
  runtime.

AI Town is a virtual town where AI characters live, chat, and socialize. It is
included as a Git submodule so its original source and Vifu integration history
remain visible together.

### [Agentshire](games/agentshire)

- **Original project:** [vifudotdev/Agentshire](https://github.com/vifudotdev/Agentshire)
- **Play on VifuHub:** [Open Agentshire](https://vifu.ai/damon/agentshire)
- **Runtime model:** An OpenClaw/QClaw plugin that maps agents to social NPCs
  in a browser-based 3D town, with a WebSocket event bridge, town editor, and
  character workshop.

Agentshire is included as a Git submodule so its plugin, bridge, and 3D town
frontend retain their own source history.

### [Microverse](games/microverse)

- **Original project:** [KsanaDock/Microverse](https://github.com/KsanaDock/Microverse)
- **Play on VifuHub:** [Open Microverse](https://vifu.ai/damon/microverse)
- **Runtime model:** A Godot 4 multi-agent social sandbox where autonomous
  characters talk, form memories, plan tasks, and move through a shared
  workplace.

The Vifu-maintained fork is included as a Git submodule so the Godot project
and its integration work retain their own source history.

## Starters

### [Hello Web](starters/hello-web)

A first-party static browser starter for testing the smallest Vifu deployment
shape:

```bash
vf manifest check --dir starters/hello-web
vf deploy starters/hello-web
```

When you are already inside a game or starter directory, the path is optional:

```bash
vf manifest check
vf deploy
```

## Vifu Integration

For a custom web game, at minimum:

- `manifest.json` with a `name`
- a browser entry point such as `index.html`
- a static build output directory

For managed source runtimes, prefer convention over configuration. A single
APKG Anki project should not need a manifest unless it wants to override the
default runtime behavior.

Vifu Hub is the platform interface from game code. It covers AI agents and
tools, game state, runtime resources, world sessions, events, and other
host-approved capabilities. For example:

```js
import * as hub from "@vifu/hub";

const result = await hub.ai.generateText({
  model: "basic",
  messages: [{ role: "user", content: "Give the player a short hint." }]
});
```

Do not call external AI or backend APIs directly from deployed game JavaScript.
Vifu Hub keeps identity, model routing, quota, runtime policy, and host
transport outside the game bundle.

## Deploy Rules

`vf deploy` validates the built output before upload.

Allowed:

- bundled JavaScript
- local assets in the build output
- Google Fonts
- approved pinned static CSS, fonts, images, and media from package CDNs
- ordinary external links
- Vifu Hub calls for AI and backend services

Blocked:

- CDN JavaScript
- remote `import(...)`, `importScripts(...)`, or Worker scripts
- remote `.js`, `.mjs`, or `.wasm` URLs
- direct calls to external AI/backend APIs
- local-only providers such as LM Studio or Ollama in deployed builds

If deploy fails, the CLI prints the built file, line, rule, URL, and suggested
fix.

## Add A Game

1. Link the original GitHub project and preserve its license and notices.
2. Integrate the project with Vifu's publish and runtime flow while preserving
   its game identity and core play loop.
3. Declare the game in `manifest.json` and let Vifu infer common build settings.
4. Use Vifu Hub as the game-to-platform interface for AI, state, resources, and
   other capabilities the game needs.
5. Keep optional local or third-party AI providers out of the deployed bundle.
6. Run `vf deploy`.

For upstream projects with meaningful history, keep the game in its own
repository and include it as a Git submodule. That makes the integration history easy
to inspect.

## Collection Principles

- Each game or starter should be runnable with `vf deploy <path>`.
- Public manifests identify games and configure runtime behavior. Managed source projects
  should start from files and add metadata only when it changes behavior or
  presentation.
- Entries identify their original GitHub project and describe their Vifu-native
  integration.
- Projects should keep deterministic local fallbacks where useful, but deployed
  builds should use Vifu Hub calls for platform services.

## License

Unless otherwise noted, Vifu-authored code in this repository is
licensed under the MIT License.

Third-party projects, Git submodules, assets, and upstream projects keep their
own licenses and notices.
