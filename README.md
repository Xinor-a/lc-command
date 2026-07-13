# 📋 lc — line-copy

Pipe any command's output into `lc`, interactively pick one or more lines,
and copy them to your clipboard.

## ✨ Features

- Interactive TUI with arrow-key navigation
- Multi-select with preserved selection order
- Copies to both **CLIPBOARD** and **PRIMARY** selections (Linux)
- Auto-detects clipboard tool: `xclip`, `xsel`, `wl-copy`, `pbcopy`, `clip.exe`
- Smart auto-quoting for items containing spaces or shell special characters

## 📦 Install

```bash
chmod +x lc
cp lc ~/.local/bin/   # or anywhere on your PATH
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

## ⚙️ Options

### `--quote <mode>`

Controls how each selected item is quoted when joined. Default is `auto`.

| Mode     | Behavior                                                                |
| -------- | ----------------------------------------------------------------------- |
| `auto`   | Quote only items that need it; prefer `'single'`, fall back to `"double"` |
| `single` | Wrap every item in single quotes                                        |
| `double` | Wrap every item in double quotes                                        |
| `none`   | No quoting                                                              |

```bash
# auto (default) — only "my file.txt" gets quoted
ls -1 | lc
# => 'my file.txt' main

# force double quotes on everything
git branch | lc --quote double
# => "main" "develop"
```

## ⌨️ Keys

| Key       | Action                                           |
| --------- | ------------------------------------------------ |
| `↑` / `↓` | Navigate                                         |
| `Enter`   | Toggle select / deselect (numbered in selection order) |
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
| Git Bash (Win) | `clip.exe`           |

## 📄 License

MIT
