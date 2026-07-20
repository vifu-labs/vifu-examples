# Awesome Open Source AI Native Games

A curated collection of open-source AI-native games and browser starters. Every
entry links to its original project and a playable build.

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

### [AIventure](https://github.com/chenyanming/AIventure)

- **Original project:** [bebechien/AIventure](https://github.com/bebechien/AIventure)
- **Play:** [Open AIventure](https://vifu.ai/damon/AIventure)

AIventure is a multiplayer adventure game where players explore a persistent
world with AI-driven characters. Its source remains available as a Git
submodule.

### [AI Town](https://github.com/chenyanming/ai-town)

- **Original project:** [a16z-infra/ai-town](https://github.com/a16z-infra/ai-town)
- **Play:** [Open AI Town](https://vifu.ai/damon/ai-town)

AI Town is a virtual town where AI characters live, chat, and socialize. Its
source remains available as a Git submodule.

### [AI Death Game](https://github.com/chenyanming/ai-death-game)

- **Original project:** [yami-inc/ai-death-game](https://github.com/yami-inc/ai-death-game)
- **Play:** [Open AI Death Game](https://vifu.ai/damon/ai-death-game)

AI Death Game is a narrative survival game where five AI characters debate,
betray, and vote while the player directs the game as its GM.

### [Agentshire](https://github.com/chenyanming/Agentshire)

- **Original project:** [Agentshire/Agentshire](https://github.com/Agentshire/Agentshire)
- **Play:** [Open Agentshire](https://vifu.ai/damon/agentshire)
- **Runtime model:** An OpenClaw/QClaw plugin that maps agents to social NPCs
  in a browser-based 3D town, with a WebSocket event bridge, town editor, and
  character workshop.

Agentshire is included as a Git submodule so its plugin, bridge, and 3D town
frontend retain their own source history.

### [Microverse](https://github.com/chenyanming/Microverse)

- **Original project:** [KsanaDock/Microverse](https://github.com/KsanaDock/Microverse)
- **Play:** [Open Microverse](https://vifu.ai/damon/microverse)
- **Runtime model:** A Godot 4 multi-agent social sandbox where autonomous
  characters talk, form memories, plan tasks, and move through a shared
  workplace.

The maintained fork is included as a Git submodule so the Godot project retains
its own source history.

## Starters

### [Hello Web](starters/hello-web)

A minimal static browser starter:

```bash
vf manifest check --dir starters/hello-web
vf deploy starters/hello-web
```

When you are already inside a game or starter directory, the path is optional:

```bash
vf manifest check
vf deploy
```

## Runtime Requirements

For a custom web game, at minimum:

- `manifest.json` with a `name`
- a browser entry point such as `index.html`
- a static build output directory

Keep a game self-contained: bundle its code and local assets with the static
output, and use the host runtime for services it provides.

## Deploy Rules

`vf deploy` validates the built output before upload.

Allowed:

- bundled JavaScript
- local assets in the build output
- Google Fonts
- approved pinned static CSS, fonts, images, and media from package CDNs
- ordinary external links
- host runtime calls for AI and backend services

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
2. Preserve the game identity and core play loop.
3. Declare the game in `manifest.json`.
4. Build a static output directory.
5. Run `vf deploy`.

For upstream projects with meaningful history, keep the game in its own
repository and include it as a Git submodule. That makes the integration history easy
to inspect.

## Collection Principles

- Each game or starter should be runnable with `vf deploy <path>`.
- Public manifests identify games and configure runtime behavior. Managed source projects
  should start from files and add metadata only when it changes behavior or
  presentation.
- Entries identify their original GitHub project and describe the game itself.
- Projects should keep deterministic local fallbacks where useful and use host
  runtime calls for available platform services.

## License

Unless otherwise noted, code authored for this collection is licensed under the
MIT License.

Third-party projects, Git submodules, assets, and upstream projects keep their
own licenses and notices.
