<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [pycharm-to-vscode-transition](#pycharm-to-vscode-transition)
- [Table of contents](#table-of-contents)
- [Settings](#settings)
    - [Enable indexing (better auto -suggestions and -import)](#enable-indexing-better-auto--suggestions-and--import)
    - [Increase depths for import suggestions](#increase-depths-for-import-suggestions)
    - [Make speed scroll closer to one in PyCharm](#make-speed-scroll-closer-to-one-in-pycharm)
    - [Make line height (interval between the lines) closer to one in PyCharm](#make-line-height-interval-between-the-lines-closer-to-one-in-pycharm)
    - [Enable auto save for files](#enable-auto-save-for-files)
    - [Add project root, src and tests dir to `PYTHONPATH` by default](#add-project-root-src-and-tests-dir-to-pythonpath-by-default)
    - [Use black formatter by default](#use-black-formatter-by-default)
- [Keybinds](#keybinds)
    - [Fix IntelliJ IDEA Keybinds extension](#fix-intellij-idea-keybinds-extension)
    - [Add line below and move cursor down](#add-line-below-and-move-cursor-down)
    - [Comment line and move cursor down](#comment-line-and-move-cursor-down)
- [Extensions](#extensions)
    - [IntelliJ IDEA Keybindings](#intellij-idea-keybindings)
    - [PyColonize — automatically add colon at the end of the line](#pycolonize--automatically-add-colon-at-the-end-of-the-line)
  - [Helpers](#helpers)
    - [multi-command — for Comment line and move cursor down](#multi-command--for-comment-line-and-move-cursor-down)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# pycharm-to-vscode-transition
Make a smooth transition from slow and heavy PyCharm to fast and light VSCode.

- `⌘` — Command (Ctrl on Windows/Linux)
- `⌃` — Ctrl
- `⌥` — Option / Alt
- `⇧` — Shift
# Table of contents

- [pycharm-to-vscode-transition](#pycharm-to-vscode-transition)
- [Settings](#settings)
    - [Enable indexing (better auto -suggestions and -import)](#enable-indexing-better-auto--suggestions-and--import)
    - [Increase depths for import suggestions](#increase-depths-for-import-suggestions)
    - [Make speed scroll closer to one in PyCharm](#make-speed-scroll-closer-to-one-in-pycharm)
    - [Make line height (interval between the lines) closer to one in PyCharm](#make-line-height-interval-between-the-lines-closer-to-one-in-pycharm)
    - [Enable auto save for files](#enable-auto-save-for-files)
    - [Add project root, src and tests dir to `PYTHONPATH` by default](#add-project-root-src-and-tests-dir-to-pythonpath-by-default)
    - [Use black formatter by default](#use-black-formatter-by-default)
- [Keybinds](#keybinds)
    - [Fix IntelliJ IDEA Keybinds extension](#fix-intellij-idea-keybinds-extension)
    - [Add line below and move cursor down](#add-line-below-and-move-cursor-down)
    - [Comment line and move cursor down](#comment-line-and-move-cursor-down)
- [Extensions](#extensions)
    - [IntelliJ IDEA Keybinding](#intellij-idea-keybindings)
    - [PyColonize — automatically add colon at the end of the line](#pycolonize--automatically-add-colon-at-the-end-of-the-line)
  - [Helpers](#helpers)
    - [multi-command](#multi-command--for-comment-line-and-move-cursor-down)

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
    },
    "code-runner.executorMap": {
        "python": "PYTHONPATH=${workspaceFolder}:${workspaceFolder}/src:${workspaceFolder}/tests ${pythonPath} -u ${fullFileName}"
    },
    "python.envFile": "~/.vscode/.env",
```
Then create `~/.vscode/.env`:
```bash
PYTHONPATH=${env:PROJ_DIR}:${env:PROJ_DIR}/src:${env:PROJ_DIR}/tests:${env:PYTHONPATH}
```
**Note:** change colons to semicolons on Windows and `.osx` to `.<your system>`
### Use black formatter by default
```json
    "[python]": {
        "editor.defaultFormatter": "ms-python.black-formatter"
    },
```
**Note:** requires [Black Formatter](https://marketplace.visualstudio.com/items?itemName=ms-python.black-formatter) extension.

# Keybinds
### Fix IntelliJ IDEA Keybinds extension
Remove it's bind for `⌘` `K` as it's a special combination in VSCode
```json
      {
        "key": "cmd+k",
        "command": "-git.commitAll",
        "when": "!inDebugMode && !terminalFocus"
      }
```
### Add line below and move cursor down
```json
      {
        "key": "cmd+enter",
        "command": "editor.action.insertLineAfter",
        "when": "editorTextFocus && !editorReadonly && editorLangId != 'python'"
      },
```
**Note:** for auto colons see [Extensions](#extensions) -> PyColonize

### Comment line and move cursor down
```json
    {
        "key": "cmd+/",
        "command": "extension.multiCommand.execute",
        "args": {
          "sequence": [
            "editor.action.commentLine",
            "cursorDown"
          ]
        },
        "when": "editorTextFocus && !editorReadonly"
      }
```
**Note:** requires [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command) extension.




# Extensions
### [IntelliJ IDEA Keybindings](https://marketplace.visualstudio.com/items?itemName=k--kato.intellij-idea-keybindings)
See [Keybinds](#keybinds) to learn more.
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

## Helpers
### [multi-command](https://marketplace.visualstudio.com/items?itemName=ryuta46.multi-command) — for [Comment line and move cursor down](#comment-line-and-move-cursor-down)
