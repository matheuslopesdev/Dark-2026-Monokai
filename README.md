# Dark 2026 Monokai

VS Code's **2026 Dark** workbench with **Monokai** syntax colors.

2026 Dark has the better UI chrome — near-black `#121314` surfaces, low-contrast borders, a calm teal accent, and fully redrawn diff, peek, chat and terminal palettes. Monokai has the better code colors — pink keywords, green declarations, orange parameters, purple literals. This theme is exactly that pairing, and nothing else.

## What it does

| Layer | Source |
| --- | --- |
| Workbench: sidebar, tabs, status bar, panels, terminal, editor background, gutter, cursor | 2026 Dark |
| Syntax: keywords, types, functions, strings, numbers, comments, markup | Monokai |

## Why it's a theme and not settings

The same result can be approximated with `editor.tokenColorCustomizations` in `settings.json`, but TextMate scope resolution picks the **most specific** matching selector, not the last one loaded. The default themes define narrow selectors such as `storage.modifier` that outrank Monokai's broader `storage` rule, so `public` and friends keep their original color no matter what order the customizations are in. Working around that takes ~170 mirrored override rules plus separate `semanticTokenColorCustomizations` — and it still breaks whenever either upstream theme adds a selector.

Shipping a real theme sidesteps the whole problem: one `tokenColors` array, no precedence contest.

Semantic highlighting is enabled, but no `semanticTokenColors` are defined — semantic tokens fall back to TextMate scope mapping, which is what Monokai itself does. Without that, the default semantic colors would override the Monokai palette in any language with a semantic token provider.

## Install

From the Marketplace: search **Dark 2026 Monokai**, or

```
code --install-extension matheuslopesdev.dark-2026-monokai
```

Then <kbd>Cmd</kbd>+<kbd>K</kbd> <kbd>Cmd</kbd>+<kbd>T</kbd> and pick **Dark 2026 Monokai**.

## Credits

Derived from two MIT-licensed themes bundled with [Visual Studio Code](https://github.com/microsoft/vscode):

- `theme-defaults` (2026 Dark) — © Microsoft Corporation
- `theme-monokai` — © Microsoft Corporation, based on the Monokai color scheme by Wimer Hazenberg

This extension is not affiliated with or endorsed by Microsoft.
