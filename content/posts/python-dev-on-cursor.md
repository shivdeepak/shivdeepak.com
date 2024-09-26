+++
title = 'Python Development on Cursor'
date = 2024-09-25T22:06:23-07:00
draft = false
type = "post"
+++

I am trying to move from Emacs to Cursor.

I love Emacs, and I cannot live without Magit, but I have also reached a point where I want to try something new and fast to setup than Emacs. 
This is the same reason why I moved from Arch Linux to Mac OS back in 2011. Maintaing your code editor should not be a full time job. Haha!

But, you know what, I might go back to Emacs, if I miss it too much.

Cursor is built on top of VS Code. So, what I am going to write here will also work on VS Code.

I am spending a lot of time writing Python these days, and I want my code editor to have good support for Python.

The bare minimum I want is:

- Syntax highlighting (do I have to mention it? :D)
- Intellisense
- Ctags style code navigation
- Auto Linting and formatting 
- Type Checking

And, here are a list of plugins that will help me to get the above features.

1. [Python ms-python.python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)

Standard VS Code extension for Python for Python Support. This will atleast give you syntax highlighting.

Once you install this extension, you can select your python environment by typing `Python: Select Interpreter` in the command palette (Ctrl+Shift+P).

2. [Pylance ms-python.vscode-pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)

Pylance is great for type checking, and it's also the default extension VS Code installs for you when you install Python extension.

Pylance will also give you code navigation and intellisense, if you select the right python interpreter in the previous step.

To enable type checking, add the following to your VS Code `settings.json` file.

```python
{
    "python.analysis.typeCheckingMode": "basic",
}
```

3. [Ruff charliermarsh.ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff)

This is the fastest formatter and linter for Python written in Rust. You don't need to install any other formatter or linter.

To enable the linter and farmatter, add the following to your VS Code `settings.json` file.

```json
{
  "[python]": {
    "editor.formatOnSave": true,
    "editor.codeActionsOnSave": {
      "source.fixAll": "explicit",
      "source.organizeImports": "explicit"
    },
    "editor.defaultFormatter": "charliermarsh.ruff"
  }
}
```

Just 3 extensions, and you are good to go.
