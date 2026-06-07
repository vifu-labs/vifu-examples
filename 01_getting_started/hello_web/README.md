# Hello Web

The smallest deployable Vifu web app.

```bash
vifu manifest check --dir 01_getting_started/hello_web
vifu deploy --dir 01_getting_started/hello_web
```

This example has no build step. Vifu uploads the directory as a static web runtime and uses `index.html` as the entry point.
