[![MELPA](https://melpa.org/packages/lusty-explorer-badge.svg)](https://melpa.org/#/lusty-explorer)
[![MELPA Stable](https://stable.melpa.org/packages/lusty-explorer-badge.svg)](https://stable.melpa.org/#/lusty-explorer)

# Usage:

Copy `lusty-explorer.el` somewhere in your `load-path`, or if if you use MELPA, then:

```
M-x package-install
=> Install package: lusty-explorer
```

Add this line to your `~/.emacs.d/init.el`:

```elisp
(require 'lusty-explorer)
```

To launch `lusty`:

```
M-x lusty-buffer-explorer
M-x lusty-file-explorer
```

And then use as you would `switch-to-buffer`  or `find-file` or `ido-find-file`. Files/buffers are filtered using the [LiquidMetal](https://github.com/rmm5t/liquidmetal) fuzzy/flex matching algorithm. Dotfiles are hidden by default but you can show them by entering `.`.

Keybindings to navigate matches:
* `TAB` - choose the highlighted item; open a file or buffer, descend into a directory
* `RET` - ditto, but create the file/buffer if there are no matches
* `C-n` / `C-p` - highlight next item, previous item in the current column
* `C-f` / `C-b` - highlight next column, previous column
* `C-s` / `C-r` - ditto
* `C-x d` - Launch `dired` within the current directory
* `C-x e` - Create a new buffer with the entered name
* Evil bindings: `j`, `k`, `C-f`, `C-b`

If you add `(lusty-explorer-mode)` to your `~/.emacs.d/init.el`, these global bindings take effect:
* `C-x b` - `lusty-buffer-explorer` (in place of `switch-to-buffer`)
* `C-x f` - `lusty-file-explorer` (in place of `find-file`)


# Customization:

To modify the keybindings, use something like:

```elisp
(add-hook 'lusty-setup-hook 'my-lusty-hook)
(defun my-lusty-hook ()
  (define-key lusty-mode-map "\C-j" 'lusty-highlight-next))
```

Respects these variables:

```elisp
completion-ignored-extensions
```


# Recent changes:

## Spring 2020:

#### Bringing this old package closer to the conventions and quality-of-life standards of Emacs packages of 2020
* Presentation:
  * The buffer/window for displaying matches properly stretches the full frame and resizes itself more exactly.
  * Look-and-feel changes in the spirit of e.g. [which-key](https://github.com/justbur/emacs-which-key) and [Hydra](https://github.com/abo-abo/hydra).
* Robustness:
  * If the package crashes or exits in an unexpected way, it cleans itself up;
  * Can now dismiss `lusty` when the matches window is selected using `q` or `C-g` or `ESC ESC ESC`;
* Correctness:
  * Buffer recency is according to the ordering of the current frame rather than the global ordering;
* Performance improvements for working in directories having many thousands of files;


# Contributors:

- Tassilo Horn
- Jan Rehders
- Hugo Schmitt
- Volkan Yazici
- René Kyllingstad
- Alex Schroeder
- Sasha Kovar
- John Wiegley
- Johan Walles
- p3r7
- Nick Alcock
- Jonas Bernoulli


# Misc:

- [Vim version](https://github.com/sjbach/lusty)
- [EmacsWiki](https://www.emacswiki.org/cgi-bin/wiki/LustyExplorer)
