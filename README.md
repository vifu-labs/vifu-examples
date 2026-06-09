# Vifu Examples

This is a collection of examples for [Vifu](https://vifu.app). Use these examples to learn how to build, adapt, and deploy AI-native web games and apps.

## Usage

Clone this repo with submodules, then install the Vifu CLI:

```bash
git clone --recurse-submodules https://github.com/vifu-labs/vifu-examples
cd vifu-examples
```

If you already cloned it without submodules:

```bash
git submodule update --init --recursive
```

Then run an example much like you would run an ordinary local web project:

```bash
vifu manifest check --dir 01_getting_started/hello_web
vifu deploy 01_getting_started/hello_web
```

The examples are organized into numbered folders based on the concept they teach. Start with `01_getting_started`, then move into external AI game adoption.

## Examples

- [**`01_getting_started/`**](01_getting_started) shows the smallest deployable Vifu web app shape.
- [**`02_external_ai_games/`**](02_external_ai_games) shows how to bring existing AI-native games to Vifu without rewriting them.

## Design Principles

- Each example should be runnable with `vifu deploy <example>`.
- Public manifests should use creator-facing nouns such as `main`, `build`, `ai`, `data`, `bundle`, and `links`.
- External projects with meaningful upstream history should stay in their own repositories and be included as Git submodules.
- Examples should keep local deterministic fallbacks where possible, so they remain inspectable outside a Vifu host.

## License

Unless otherwise noted, Vifu-authored example code in this repository is licensed under the MIT License.

Third-party examples, Git submodules, assets, and upstream projects keep their own licenses and notices.
