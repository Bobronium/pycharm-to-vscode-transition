# pycharm-to-vscode-transition
Make a smooth transition from slow and heavy PyCharm to fast and light VSCode.

- `⌘` — Command (Ctrl on Windows/Linux)
- `⌃` — Ctrl
- `⌥` — Option / Alt
- `⇧` — Shift

# Settings
### Enable indexing (better auto -suggestions and -import)
```json
"python.analysis.indexing": true,
```
### Increase depths for import suggestions
```json
"python.analysis.packageIndexDepths":[
        ["", 2],
        ["package_name", 3],
    ]
```
**Note:** Requires Pylance, **explanation:** https://github.com/microsoft/pylance-release/issues/291#issuecomment-1015880138
### Make speed scroll closer to one in PyCharm
```json
"editor.mouseWheelScrollSensitivity": 0.35,
```
Tested on MacBook's touchpad

### Make line height (interval between the lines) closer to one in PyCharm
```json
"editor.lineHeight": 1.85,
```

### Enable auto save for files
```json
"files.autoSave": "afterDelay"
```

### Add project root, src and tests dir to `PYTHONPATH` by default
```json
"terminal.integrated.env.osx": {
  "PYTHONPATH": "${workspaceFolder}:${workspaceFolder}/src:${workspaceFolder}/tests"
}
```
**Note:** change colons to semicolons on Windows and `.osx` to `.<your system>`
### Use black formatter by default
```json
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter"
    },
```
**Note:** requires [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter) extension.



# Extensions
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
