# pycharm-to-vscode-transition
Make a smooth transition from slow and heavy PyCharm to fast and light VSCode.

- `⌘` — Command (Ctrl on Windows/Linux)
- `⌃` — Ctrl
- `⌥` — Option / Alt
- `⇧` — Shift


### [PyColonize](https://marketplace.visualstudio.com/items?itemName=fertigt.pycolonize) — automatically add colon at the end of the line
<img align="left" width="200" alt="animated" src="https://user-images.githubusercontent.com/36469655/164995767-a37163c3-ddf0-400f-a45c-e85e5c798c40.gif">

- `⌘` `Enter` — add colon and continue on the new line
- `⇧` `Enter` — add colon and continue on the same line
- `⌘` `⌥` `Enter` — add colon and stay at the same position

By default shortcut will work only with Python files. If you want to mimic this behaviour in other languages as well, but without a colon, add following to `keybindings.json`:
```json
      {
        "key": "cmd+enter",
        "command": "editor.action.insertLineAfter",
        "when": "editorTextFocus && !editorReadonly && editorLangId != 'python'"
      }
```
