# Hyper-claude
This is a claude code clone.

This is not sponsered by claude.
I vibe coded this so it will have some bugs but the issues will be solved by me (human).

# HyperClaude TUI

⚡ **runs anywhere. uses anything.** — A terminal-UI port of the HyperClaude web interface.

A full-featured TUI chat client built with [Textual](https://textual.textualize.io/), supporting any OpenAI-compatible API plus Anthropic and Google Gemini.

## Features

- 🗂  **Sidebar** with chat sessions grouped by date (Today / Yesterday / Week / Older), toggleable with `Ctrl+B`
- 🤖  **Multi-provider** — OpenAI, Anthropic, Google Gemini, DeepSeek, OpenRouter, Groq, Ollama, custom OpenAI-compatible
- 🔥  **Streaming** responses with live markdown rendering
- 🎨  **Light & dark themes** (toggle with `Ctrl+T`)
- 🪄  **Slash commands** with autocomplete palette: `/help`, `/clear`, `/model`, `/system`, `/tokens`, `/export`, `/theme`, `/reset` and more
- ⚙️   **Settings modal** for provider, API key, base URL, model, system prompt, temperature, max tokens, streaming
- 👋  **Welcome screen** with quick-prompt cards
- 💾  **Persistent storage** in `~/.hyperclaude/`
- 📦  **Export** chat as JSON
- ⌨️   **Keyboard-first** — full set of shortcuts; Footer shows them all

## Install

```bash
pip install -r requirements.txt
```

## Run

```bash
python hyperclaude.py
```

On first launch:
1. Press `Ctrl+,` (or click the ⚙ icon) to open Settings
2. Pick a provider, paste your API key, save
3. Start chatting — `Ctrl+Enter` to send, `Enter` for newline

For free local inference, install [Ollama](https://ollama.com/) and pick provider = `ollama`. No API key needed.

## Keyboard shortcuts

| Key            | Action            |
|----------------|-------------------|
| `Ctrl+Enter`   | Send message      |
| `Enter`        | New line          |
| `Ctrl+N`       | New chat          |
| `Ctrl+B`       | Toggle sidebar    |
| `Ctrl+M`       | Pick model        |
| `Ctrl+,`       | Open settings     |
| `Ctrl+T`       | Toggle theme      |
| `Ctrl+E`       | Export chat       |
| `Ctrl+L`       | Clear chat        |
| `Ctrl+Q`       | Quit              |
| `/`            | Slash commands    |

## Slash commands

`/help` `/clear` `/new` `/sessions` `/provider` `/model [name]` `/export` `/system [prompt]` `/bash` `/file` `/search` `/compact` `/tokens` `/theme` `/reset` `/quit`

## Files

- `hyperclaude.py` — single-file app
- `~/.hyperclaude/settings.json` — your config
- `~/.hyperclaude/sessions.json` — chat history
- `~/.hyperclaude/export-*.json` — exported chats

## Notes on the port

Where the web version uses CSS/JS effects, the TUI maps them to Textual equivalents:

| Web                              | TUI                                       |
|----------------------------------|-------------------------------------------|
| Sidebar slide animation          | `display: none` toggle on sidebar         |
| Model dropdown                   | `ModelPicker` modal                       |
| Settings modal                   | `SettingsModal` modal                     |
| Streaming cursor blink           | Live `Markdown.update()` on each chunk    |
| Tool-use collapsible blocks      | Markdown sections with code fences        |
| Toast notifications              | `app.notify(...)`                         |
| Theme via CSS variables          | `app.theme = "textual-dark/light"`        |
| LocalStorage                     | JSON files under `~/.hyperclaude/`        |
| HTTP via `fetch`                 | `httpx.AsyncClient` (streaming SSE)       |


