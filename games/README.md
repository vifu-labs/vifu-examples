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
