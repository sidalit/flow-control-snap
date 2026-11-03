<div align="center">

<img src="snap/gui/flow-control.png" alt="Flow Control logo" width="128" />

# Flow Control

**A fast terminal text editor for programmers**

[![flow-control](https://snapcraft.io/flow-control/badge.svg)](https://snapcraft.io/flow-control)
[![Base: core26](https://img.shields.io/badge/Base-core26-2C8C3C?logo=canonical&logoColor=white)](https://snapcraft.io/core26)
![Confinement: strict](https://img.shields.io/badge/Confinement-strict-2C8C3C)
[![Maintainer: sidaliteir](https://img.shields.io/badge/Maintainer-sidaliteir-2C8C3C?logo=snapcraft&logoColor=white)](https://snapcraft.io/publisher/sidaliteir)
![Architectures: amd64 and arm64](https://img.shields.io/badge/Architectures-amd64%20%7C%20arm64-2C8C3C?logo=linux&logoColor=white)

[Getting Started](#getting-started) · [Configure](#configure) · [Limitations](#limitations) · [Build](#build) · [Support](#support) · [License](#license)

Unofficial snap packaging for [Flow Control](https://github.com/neurocyte/flow), a programmer's text editor for the terminal with tree-sitter syntax highlighting, multiple cursors and Flow, Emacs, Vim and Helix keybinding modes.

</div>

---

## Getting Started

<a href="https://snapcraft.io/flow-control"><img alt="Get it from the Snap Store" src="https://snapcraft.io/en/dark/install.svg" width="180"></a>

```bash
sudo snap install flow-control
flow-control ~/notes.md
```

The upstream command is called `flow`. To use that name, create an alias:

```bash
sudo snap alias flow-control flow
flow src/main.c:120
```

Press `F1` for the manual, `Ctrl+Shift+P` or `Alt+X` for the command palette, `Ctrl+F2` for the list of keybindings and `F4` to switch between the Flow, Emacs, Vim and Helix keybinding modes.

Use a terminal with 24-bit color, a [Nerd Font](https://www.nerdfonts.com) and a UTF-8 locale. Kitty, Foot and Ghostty work best.

## Configure

Flow Control has no snap options. Settings, keybindings, themes and file types are changed from the editor: run the commands that start with `Edit` in the command palette.

| Data | Location |
| --- | --- |
| Configuration | `~/snap/flow-control/current/.config/flow` |
| Logs and recent files | `~/snap/flow-control/current/.local/state/flow` |
| Cache | `~/snap/flow-control/current/.cache/flow` |

Run `flow-control --help` for the command-line options and `flow-control --list-languages` for the supported languages.

For `/media` or `/mnt`, connect `sudo snap connect flow-control:removable-media`.

## Limitations

- Language servers, formatters and other programs installed on your computer cannot be started from the editor. Code completion, diagnostics, go to definition and formatting through them are not available, and shell commands run from the editor are limited to the tools included in the snap.
- git and ripgrep are included, so git status, the project file list and find in files work. Your `~/.gitconfig` is not read.
- Hidden files directly under your normal home directory are inaccessible.
- An existing `~/.config/flow` from a non-snap install is not used. Copy it to `~/snap/flow-control/current/.config/flow` to keep your settings.
- Restarting the editor as root (`sudo`) is not supported.
- Copy and paste use the terminal clipboard (OSC 52), so your terminal must support it.

## Build

```bash
git clone https://github.com/sidalit/flow-control-snap.git
cd flow-control-snap
sudo snap install snapcraft --classic
snapcraft pack
```

Release builds use Zig 0.15.2; HEAD builds use Zig 0.17.0. Both toolchains are downloaded from ziglang.org with checksum verification.

## Support

- **Installation or snap issues:** [open a packaging issue](https://github.com/sidalit/flow-control-snap/issues).
- **Application bugs:** [report them upstream](https://github.com/neurocyte/flow/issues).

## License

Snap packaging: [MIT](https://github.com/sidalit/flow-control-snap/blob/main/LICENSE).
