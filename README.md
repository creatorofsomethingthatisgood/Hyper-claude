# HyperClaude TUI

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10+-blue?logo=python&style=flat" alt="Python">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20macOS%20%7C%20Windows-blue?logo=windows&style=flat" alt="Platform">
  <img src="https://img.shields.io/badge/License-MIT-green?logo=open-source-initiative&style=flat" alt="License">
</p>

<p align="center">
  ⚡ <strong>runs anywhere. uses anything.</strong>
</p>

A powerful, keyboard-driven terminal UI chat client built with [Textual](https://textual.textualize.io/). Connect to OpenAI, Anthropic, Google Gemini, DeepSeek, Ollama, or any OpenAI-compatible API — all from your terminal.

---

## Why HyperClaude TUI?

- **🔌 Works with everything** — OpenAI, Anthropic, Google Gemini, DeepSeek, OpenRouter, Groq, Ollama, or any custom OpenAI-compatible endpoint
- ⚡ **Lightning fast** — Single Python file, zero dependencies outside the core libs
- 🎯 **Keyboard-first** — Never touch your mouse. Every action has a shortcut
- 🌙 **Beautiful themes** — Light and dark mode with live toggle
- 💾 **Your data stays yours** — Local JSON storage, no cloud sync, no account needed
- 🖥️ **Cross-platform** — Linux, macOS, Windows. Even has a standalone .exe

---

## Quick Start

### macOS / Linux

```bash
# Clone or download
cd hyperclaude-tui

# Install dependencies
pip install -r requirements.txt

# Run
python hyperclaude.py
```

### Windows

**Option 1:** Download the standalone `.exe` from [Releases](https://github.com/anthropics/hyperclaude-tui/releases) — no Python needed!

**Option 2:** Build from source:

```cmd
pip install pyinstaller textual httpx
pyinstaller hyperclaude.spec --noconfirm
```

---

## First Run

1. Launch the app
2. Press `Ctrl+,` (or click the ⚙️ icon) to open Settings
3. Choose your provider:
   - **Ollama** — Free local inference (install from [ollama.ai](https://ollama.com/))
   - **OpenAI** — OpenAI API key from [platform.openai.com](https://platform.openai.com/)
   - **Anthropic** — Anthropic API key from [console.anthropic.com](https://console.anthropic.com/)
   - **Other** — Any OpenAI-compatible endpoint (DeepSeek, local LLMs, etc.)
4. Enter your API key and select a model
5. Press `Ctrl+Enter` to send your first message!

> **Tip:** Press `/` to see all available slash commands

---

## Supported Providers

| Provider | API Key Required | Notes |
|----------|------------------|-------|
| Ollama | ❌ | Free local inference |
| OpenAI | ✅ | GPT-4, GPT-4o, GPT-4o-mini |
| Anthropic | ✅ | Claude 3.5 Sonnet, Claude 3 Opus |
| Google Gemini | ✅ | Gemini Pro, Flash |
| DeepSeek | ✅ | DeepSeek Chat |
| OpenRouter | ✅ | Access 100+ models |
| Groq | ✅ | Fast inference |
| Custom | ✅ | Any OpenAI-compatible API |

---

## Features

### Chat Interface
- 📜 **Session history** — Chats grouped by date (Today / Yesterday / This Week / Older)
- 📝 **Live markdown** — Streaming responses rendered in real-time
- 🔄 **Auto-scroll** — Follow along as the AI responds

### Productivity
- ⌨️ **Slash commands** — `/help`, `/new`, `/clear`, `/model`, `/export`, `/system`, `/tokens`, and more
- 🔍 **Search** — Search through past conversations
- 📤 **Export** — Save chats as JSON for backup or analysis

### Customization
- 🎨 **Themes** — Light and dark mode, toggle with `Ctrl+T`
- ⚙️ **Settings** — Temperature, max tokens, system prompt, custom base URLs
- 🔑 **Multiple providers** — Switch between providers without re-entering keys

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Enter` | Send message |
| `Enter` | New line in input |
| `Ctrl+N` | Start new chat |
| `Ctrl+B` | Toggle sidebar |
| `Ctrl+M` | Model picker |
| `Ctrl+,` | Open settings |
| `Ctrl+T` | Toggle theme |
| `Ctrl+E` | Export chat |
| `Ctrl+L` | Clear current chat |
| `Ctrl+Q` | Quit |
| `Ctrl+S` | Save (in input mode) |
| `/` | Open slash command palette |
| `↑/↓` | Navigate history |
| `Tab` | Autocomplete |

---

## Slash Commands

| Command | Description |
|---------|-------------|
| `/help` | Show all commands |
| `/new` | Start new chat |
| `/clear` | Clear current chat |
| `/sessions` | List all sessions |
| `/provider [name]` | Switch provider |
| `/model [name]` | Switch model |
| `/export` | Export chat as JSON |
| `/system [prompt]` | Set system prompt |
| `/tokens` | Show token count |
| `/theme` | Toggle light/dark |
| `/reset` | Reset to defaults |
| `/quit` | Exit app |

---

## Configuration

### Files

| File | Purpose |
|------|---------|
| `hyperclaude.py` | The application (single file!) |
| `~/.hyperclaude/settings.json` | Your configuration |
| `~/.hyperclaude/sessions.json` | Chat history |
| `~/.hyperclaude/export-*.json` | Exported chats |

### Settings Location

- **Linux/macOS:** `~/.hyperclaude/`
- **Windows:** `%USERPROFILE%\.hyperclaude\`

### Example Settings

```json
{
  "provider": "ollama",
  "model": "llama3",
  "temperature": 0.7,
  "max_tokens": 4096,
  "system_prompt": "You are a helpful assistant.",
  "theme": "dark"
}
```

---

## Building for Windows

If you want to build the executable yourself:

```cmd
# Install build tools
pip install pyinstaller textual httpx

# Build
pyinstaller hyperclaude.spec --noconfirm

# Output: dist/HyperClaude.exe
```

See [BUILD.md](BUILD.md) for detailed instructions.

---

## Troubleshooting

### "Terminal doesn't support 256 colors"
- Most modern terminals support this by default
- On Windows, use Windows Terminal or ConEmu
- Check with: `python -c "import curses; curses.initscr()"`

### Ollama not connecting
- Make sure Ollama is running: `ollama list`
- Default endpoint is `http://localhost:11434`
- Can be changed in Settings → Base URL

### API key not working
- Keys are stored in `~/.hyperclaude/settings.json`
- Use `/provider` or Settings to update
- Some providers need the full key (e.g., `sk-...`)

---

## Contributing

This is a single-file application designed to be easy to modify:

1. Fork the repo
2. Edit `hyperclaude.py`
3. Submit a PR

No build system, no compilation — just Python.

---

## Credits

Built with [Textual](https://textual.textualize.io/) — the TUI framework that makes terminal apps feel like native applications.

---

## License

MIT License — free to use, modify, and distribute.

---

<p align="center">
  Made with ❤️ for the terminal enthusiasts
</p>
