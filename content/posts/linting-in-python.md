+++
title = 'Python Development on Emacs'
date = 2024-08-02T18:22:53-07:00
description = "Setting up PEP8 style checks, and auto formating for Python on Emacs"
draft = false
type = "post"


+++

I am sucker for writing consistent well formatted code. Python [PEP8](https://peps.python.org/pep-0008/) style guide is probably my most favorite thing about Python. Because Python is one of the very few programming languages ([Golang](https://go.dev/doc/effective_go#formatting) is another) that prescribe a specific style guide.

Ruby, Javascript, C, C++ and Java don't have such a prescribed style guide, and the project / organization that is using the language has to establish their own style guides.

> Formatting issues are the most contentious but the least consequential. People can adapt to different formatting styles but it's better if they don't have to, and less time is devoted to the topic if everyone adheres to the same style.

So, if a programming language prescribes a style guide then you can approach this formatting Utopia. Well atleast for Python and Golang it's possible.

In this article I am going to cover how to setup Emacs such that you can write well formatted Python code easily without having to memorize PEP8 style guide. Here are the two features needed to achieve this:

- **real time formatting checks** shows style voilations in the emacs buffer as you code.
- **auto formatting** allows you to quickly fix all style voilations in a file with a single command.

### Install Requirements

For setting up real time formatting checks, we will install `flycheck` package in emacs. And along with that we will install `flake8` python package.

And for setting up auto formating, we will need `py-autopep8` emacs package from [MELPA](https://melpa.org/#/py-autopep8). And along with that we will install `pep8` python package.


**Install Python Packages**

```shell
pip install flake8
pip install pep8
```

**Setup MELPA on Emacs**

```elisp
(require 'package)
(add-to-list 'package-archives '("melpa" . "https://melpa.org/packages/") t)
(package-initialize)
```

**Install Emacs Packages**

```elisp
;; flycheck
(unless (package-installed-p 'flycheck)
  (package-refresh-contents)
  (package-install 'flycheck))

;; autopep8
(unless (package-installed-p 'py-autopep8)
  (package-refresh-contents)
  (package-install 'py-autopep8))
```

### Configure Real-time Formatting Checks

```elisp
;; enable flycheck when python mode is enabled
(add-hook 'python-mode-hook 'flycheck-mode)

;; set location of flake8 executable
(setq flycheck-python-flake8-executable "/opt/homebrew/anaconda3/bin/flake8")

;; set flycheck checker to flake8 in python-mode
(add-hook 'python-mode-hook
          (lambda ()
            (flycheck-select-checker 'python-flake8)))

;; optionally, set a keyboard shortcut to show list of errors
(global-set-key (kbd "C-c f l") 'flycheck-list-errors)
```

### Configure Auto Formatting

```elisp
;; set location of pep8 executable
(setenv "PATH" (concat (getenv "PATH") ":/opt/homebrew/anaconda3/bin"))
(setq exec-path (append exec-path '("/opt/homebrew/anaconda3/bin")))

;; set keyboard shortcut to auto format current buffer
(define-key python-mode-map (kbd "C-c C-f") 'py-autopep8-buffer)

;; optionally, enable auto formatting on save (not recommended)
(add-hook 'python-mode-hook 'py-autopep8-enable-on-save)
```

And that's it. You are all set to start writing well formatted Python code in Emacs.
