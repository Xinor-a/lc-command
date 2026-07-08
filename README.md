# 📋 lc.sh — line-copy

Pipe any command's output into `lc.sh`, interactively pick one or more lines,
and copy them to your clipboard.

## ✨ Features

- Interactive TUI with arrow-key navigation
- Multi-select with preserved selection order
- Copies to both **CLIPBOARD** and **PRIMARY** selections (Linux)
- Auto-detects clipboard tool: `xclip`, `xsel`, `wl-copy`, `pbcopy`

## 📦 Install

```bash
chmod +x lc.sh
cp lc.sh ~/.local/bin/lc   # or anywhere on your PATH
```

On Ubuntu, make sure a clipboard tool is available:

```bash
sudo apt install xclip
```

## 🚀 Usage

```bash
git branch | lc
ls -1 | lc
docker ps --format '{{.Names}}' | lc
```

## ⌨️ Keys

| Key       | Action                                           |
| --------- | ------------------------------------------------ |
| `↑` / `↓` | Navigate                                         |
| `Enter`   | Toggle select / deselect (✔)                     |
| `d`       | **Done** — copy selected lines and exit           |
| `q`       | **Quit** — exit without copying                   |

When multiple lines are selected, they are joined with a space in the order
you selected them.

## 🖥️ Platform Support

| Platform       | Clipboard tool       |
| -------------- | -------------------- |
| Ubuntu / X11   | `xclip` or `xsel`    |
| Wayland        | `wl-copy`            |
| macOS          | `pbcopy`             |

## 📄 License

MIT
