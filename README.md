<p align="center">
  <img src="128x128@2x.png" alt="Grid Plus" width="128" height="128" />
</p>

<h1 align="center">Grid Plus</h1>

<p align="center">
  A fast, native desktop SQL client for PostgreSQL.
</p>

<p align="center">
  <a href="https://github.com/lengzuo/grid-plus/releases/latest"><img src="https://img.shields.io/github/v/release/lengzuo/grid-plus?style=flat-square&color=blue" alt="Latest Release" /></a>
  <a href="https://github.com/lengzuo/grid-plus/releases"><img src="https://img.shields.io/github/downloads/lengzuo/grid-plus/total?style=flat-square&color=green" alt="Downloads" /></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-BSL--1.1-orange?style=flat-square" alt="License" /></a>
  <img src="https://img.shields.io/badge/platform-macOS-lightgrey?style=flat-square" alt="Platform" />
</p>

---

## What is Grid Plus?

Grid Plus is a native desktop application for connecting to and managing PostgreSQL databases. Built with **Tauri v2** (Rust) and **React/TypeScript**, it delivers a lightweight, secure, and responsive experience without the overhead of Electron-based alternatives.

### Key Features

- **Multi-connection management** — Connect to multiple PostgreSQL databases simultaneously
- **Tabbed query editor** — Write and execute SQL across multiple tabs with syntax highlighting (CodeMirror 6)
- **Schema browser** — Browse tables, columns, and database objects at a glance
- **Transaction support** — Full `BEGIN`/`COMMIT`/`ROLLBACK` control per editor session
- **Virtualized results** — Handle large result sets efficiently with virtualized row rendering
- **Data export** — Export query results for further analysis
- **Auto-save** — Query buffers are automatically saved and restored across sessions
- **Secure credential storage** — Passwords are stored in the OS Keychain, never in plain text
- **Dark mode** — Full dark mode support out of the box
- **Internationalization** — Available in English and Simplified Chinese (中文)
- **Auto-updater** — Get notified when a new version is available and update in-app

---

## Screenshots

<!-- 
  TODO: Replace these with actual screenshots.
  Recommended: place images in a docs/screenshots/ folder and reference them here.
  
  Example:
  ![Query Editor](docs/screenshots/query-editor.png)
  ![Dark Mode](docs/screenshots/dark-mode.png)
-->

> Screenshots coming soon. Star the repo to stay updated!

---

## Download

### Latest Release

| Platform | Architecture | Download |
|----------|-------------|----------|
| macOS | Apple Silicon (arm64) | [Download .dmg](https://github.com/lengzuo/grid-plus/releases/latest/download/Grid.Plus_1.0.1_aarch64.dmg) |
| macOS | Intel (x64) | [Download .dmg](https://github.com/lengzuo/grid-plus/releases/latest/download/Grid.Plus_1.0.1_x64.dmg) |

> Windows and Linux builds are not yet available. Star/watch the repo to be notified when they ship.

You can also browse [all releases](https://github.com/lengzuo/grid-plus/releases) for older versions.

### Installation (macOS)

1. Download the `.dmg` file for your architecture
2. Open the `.dmg` and drag **Grid Plus** into your Applications folder
3. On first launch, macOS may warn about an unidentified developer:
   - Go to **System Settings > Privacy & Security** and click **Open Anyway**
4. Connect to your PostgreSQL database and start querying

### Auto-Updates

Grid Plus checks for updates automatically on launch. When a new version is available, you'll see an in-app notification to download and install it.

---

## Architecture

Grid Plus is built with a modern, layered architecture:

```
┌─────────────────────────────────┐
│     React + TypeScript (UI)     │  Frontend
│   CodeMirror 6 · TanStack Table │
├─────────────────────────────────┤
│        Tauri v2 IPC Bridge      │  Native boundary
├─────────────────────────────────┤
│       Rust Backend (Tokio)      │  Backend
│  Connection pools · SQL engine  │
│  Domain rules · Value mapping   │
├─────────────────────────────────┤
│     PostgreSQL · SQLite (WAL)   │  Data layer
│     OS Keychain (credentials)   │
└─────────────────────────────────┘
```

### Tech Stack

| Component | Technology |
|-----------|-----------|
| Framework | [Tauri v2](https://v2.tauri.app/) |
| Frontend | React 19 + TypeScript + Vite |
| Backend | Rust (2021 edition) |
| Database Driver | [sqlx](https://github.com/launchbadge/sqlx) (async, compile-time checked) |
| UI Components | [shadcn/ui](https://ui.shadcn.com/) (Radix primitives) |
| Styling | Tailwind CSS v4 |
| Editor | CodeMirror 6 |

### Why Tauri?

| | Tauri (Grid Plus) | Electron |
|-|-------------------|----------|
| Binary size | ~15 MB | ~150 MB+ |
| Memory usage | Low (native webview) | High (bundled Chromium) |
| Backend | Rust (memory-safe, fast) | Node.js |
| Security | OS-level webview sandbox + Rust type safety | Chromium sandbox |

---

## Supported Databases

| Database | Status |
|----------|--------|
| PostgreSQL 12+ | Supported |
| MySQL | Planned |
| SQLite | Planned |

---

## System Requirements

- **macOS** 11 (Big Sur) or later
- PostgreSQL 12+ as the target database
- ~100 MB disk space

---

## Pricing

Grid Plus offers a **free tier** with a 2-tab limit — enough for quick queries and exploration. For power users who need unlimited tabs, a license key is available.

All features (syntax highlighting, schema browser, transactions, dark mode, auto-save, etc.) are available in both tiers.

---

## Security & Privacy

- **Credentials**: Database passwords are stored exclusively in the macOS Keychain — never in config files, SQLite, or plain text
- **Local-first**: All workspace data (saved queries, tab state, connection metadata) is stored locally in a SQLite database. Nothing is sent to external servers
- **No telemetry**: Grid Plus does not collect analytics, usage data, or crash reports
- **Update check**: The only external network request (besides your database connections) is an update check against GitHub Releases

---

## Reporting Issues

Found a bug or have a feature request? Please [open an issue](https://github.com/lengzuo/grid-plus/issues/new).

When reporting a bug, include:

- Your macOS version and chip (Apple Silicon / Intel)
- Grid Plus version (found in **Settings > About**)
- Steps to reproduce the issue
- Any error messages or unexpected behavior

---

## Roadmap

- [ ] Windows and Linux support
- [ ] MySQL adapter
- [ ] SQLite adapter
- [ ] SSH tunnel connections
- [ ] Query plan visualization (`EXPLAIN ANALYZE`)

---

## License

Grid Plus is licensed under the [Business Source License 1.1](LICENSE).

| | |
|-|-|
| **Allowed** | Personal use, evaluation, non-commercial use, filing issues and feature requests |
| **Not allowed** | Commercial redistribution, hosting as a service, creating competing products from this source |
| **Change date** | 4 years after each release, the code converts to [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0) |

See the [LICENSE](LICENSE) file for the full text.

---

<p align="center">
  Built with <a href="https://v2.tauri.app/">Tauri</a> and <a href="https://www.rust-lang.org/">Rust</a>
</p>
