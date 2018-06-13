VsCode
VsCode Shortcuts:
command + p —> enter the command palette (order does not matter)
command + p —> fetch (search term / order does not matter)
command + shift + p —> more options in the command palette
command + shift + p > "git history" —> current branch or … —> all branches
option + z —> wrap code
control + ` —> open terminal
you—> hide sidebar
command + K + command + F —> auto formatter
Command + ` → open up Terminal
Close sidebars hotkey?
Split windows hotkey?

Snippets/Linter/Extensions
https://www.youtube.com/watch?v=YIvjKId9m2c
Emmet: (built into VsCode):
Linter:
https://github.com/tonsky/FiraCode
https://github.com/airbnb/javascript
Prettier settings go somewhere?
https://www.youtube.com/watch?v=YIvjKId9m2c

Eslintrc.js ← settings for linter live here. module.exports = {
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true,
        "node": true
    },
    "globals": {
    "$":true,
    },
    "extends": "eslint:recommended",
    "rules": {
        "linebreak-style": [
            "error",
            "unix"
        ]
    }
};


VsCode “user settings”  ← settings for VsCode live here.
{
    "workbench.colorTheme": "Hopscotch",
    "editor.wordWrap": "on",
    "files.autoSave": "onFocusChange",
    "workbench.iconTheme": "vscode-icons",
    "team.showWelcomeMessage": false,
    "vim.disableAnnoyingNeovimMessage": true,
    "atomKeymap.promptV3Features": true,
    "editor.multiCursorModifier": "ctrlCmd",
    "editor.formatOnPaste": true,
    "liveServer.settings.donotShowInfoMsg": true,
    "window.zoomLevel": 0,
    "editor.tabCompletion": true,
    "editor.fontSize": 15,
    "editor.renderLineHighlight": "all",
    "prettier.printWidth": 100
}


Emmet Shortcuts.
