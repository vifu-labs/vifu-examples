# Vifu Examples

This repository collects runnable examples for [Vifu](https://vifu.ai). Use it
to learn how to build, adapt, and deploy AI-native browser games and apps.

Most examples are intentionally ordinary web projects. If a game can produce a
static browser build with an `index.html`, it can usually be adapted to Vifu with
a small `manifest.json` and SDK integration.

Managed source examples should be more like Hugging Face repos: the source file
is the product, and metadata is optional. For example, an Anki project can be a
folder with an `.apkg` file that `vifu deploy` can infer and send to the
platform Anki runtime.

## Start Here

Clone with submodules:

```bash
git clone --recurse-submodules https://github.com/vifudotdev/vifu-examples
cd vifu-examples
```

If you already cloned without submodules:

```bash
git submodule update --init --recursive
```

Deploy the smallest example:

```bash
vifu manifest check --dir 01_getting_started/hello_web
vifu deploy 01_getting_started/hello_web
```

When you are already inside an example directory, the path is optional:

```bash
vifu manifest check
vifu deploy
```

## What A Vifu Game Needs

For a custom web game, at minimum:

- `manifest.json` with a `name`
- a browser entry point such as `index.html`
- a static build output directory

For managed source runtimes, prefer convention over configuration. A single
APKG Anki example should not need a manifest unless it wants to override the
default runtime behavior.

For AI-native features, use the Vifu SDK from game code:

```js
const result = await Vifu.ai.generateText({
  model: "basic",
  messages: [{ role: "user", content: "Give the player a short hint." }]
});
```

Do not call external AI or backend APIs directly from deployed game JavaScript.
The SDK is how games use Vifu auth, model routing, quota, save state, resources,
and future platform services.

## Deploy Rules

`vifu deploy` validates the built output before upload.

Allowed:

- bundled JavaScript
- local assets in the build output
- Google Fonts
- approved pinned static CSS, fonts, images, and media from package CDNs
- ordinary external links
- Vifu SDK calls for AI and backend services

Blocked:

- CDN JavaScript
- remote `import(...)`, `importScripts(...)`, or Worker scripts
- remote `.js`, `.mjs`, or `.wasm` URLs
- direct calls to external AI/backend APIs
- local-only providers such as LM Studio or Ollama in deployed builds

If deploy fails, the CLI prints the built file, line, rule, URL, and suggested
fix.

## Examples

- [`01_getting_started/`](01_getting_started) shows the smallest deployable Vifu
  web app shape.
- [`02_external_ai_games/`](02_external_ai_games) shows how to bring existing
  AI-native games to Vifu with minimal changes.

## Adapting Your Own Game

1. For a custom web game, add a V1 `manifest.json`.
2. Start with only `name`; let Vifu infer common entry and build settings.
3. Make sure the build output contains `index.html`.
4. Replace direct AI/backend calls with the Vifu SDK.
5. Keep optional local or third-party AI providers out of the deployed bundle.
6. Run `vifu deploy`.

For external projects with meaningful upstream history, keep the game in its own
repository and include it as a Git submodule. That makes the adaptation diff easy
to inspect.

## Design Principles

- Each example should be runnable with `vifu deploy <example>`.
- Public manifests are for custom runtime overrides. Managed source examples
  should start from files and add metadata only when it changes behavior or
  presentation.
- Examples should demonstrate visible product capabilities, not only internal
  plumbing.
- Examples should keep deterministic local fallbacks where useful, but deployed
  builds should use Vifu SDK calls for platform services.

## License

Unless otherwise noted, Vifu-authored example code in this repository is
licensed under the MIT License.

Third-party examples, Git submodules, assets, and upstream projects keep their
own licenses and notices.
