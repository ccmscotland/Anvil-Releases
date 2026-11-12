# Anvil User Guide and Instructions

Welcome to **Anvil**, a keyboard-first, high-performance text and code editor for Android that scales seamlessly from handheld phones to tablets, Samsung DeX workstations, and Googlebook OS laptops from a single binary.

---

## Table of Contents

- [Glossary](#glossary)
1. [Introduction and Philosophy](#1-introduction-and-philosophy)
2. [System Requirements and Installation](#2-system-requirements-and-installation)
3. [Adaptive Interfaces and Form Factors](#3-adaptive-interfaces-and-form-factors)
4. [File Operations and Getting Started](#4-file-operations-and-getting-started)
5. [Document and Tab Management](#5-document-and-tab-management)
6. [Split Views and Live Previews](#6-split-views-and-live-previews)
7. [Editing, Navigation and Cursor Superpowers](#7-editing-navigation-and-cursor-superpowers)
8. [Googlebook OS Rambler and Voice Dictation](#8-googlebook-os-rambler-and-voice-dictation)
9. [Touchpad, Mouse and Laptop Gestures](#9-touchpad-mouse-and-laptop-gestures)
10. [Languages, Grammars and Code Intelligence](#10-languages-grammars-and-code-intelligence)
11. [Snippets and New-File Templates](#11-snippets-and-new-file-templates)
12. [Built-in Text Tools and Transforms](#12-built-in-text-tools-and-transforms)
13. [Storage Locations and Remote Connections](#13-storage-locations-and-remote-connections)
14. [AI Assistant Integration](#14-ai-assistant-integration)
15. [Theming, Typography and Appearance](#15-theming-typography-and-appearance)
16. [Settings, Keymap and EditorConfig](#16-settings-keymap-and-editorconfig)
17. [Model Context Protocol (MCP) Integration](#17-model-context-protocol-mcp-integration)
18. [Comprehensive Keyboard Shortcuts Reference](#18-comprehensive-keyboard-shortcuts-reference)
19. [Troubleshooting and FAQ](#19-troubleshooting-and-faq)

---

## Glossary

Anvil uses these words the same way everywhere: in menus, dialogs, messages and this guide.

**Places**
- **Location**: any place the file drawer can browse. Add them with **Add a location** and manage them under **Locations**.
- **Location kinds**: **Device folder**, **Network share (SMB)** and **Google Drive**. Where space is short, such as the status bar or the Recent list, the kind is shortened to *This device*, *SMB* or *Google Drive*.
- **Document**: a file open in a tab. **Open documents** are the documents in your tabs.

**Verbs**
- **Disconnect**: close the connection to a server. Its settings and saved sign-in details are kept.
- **Remove**: take something off a list without destroying it. **Remove** on a location takes it off Locations and deletes any saved password or token from this device; files on the server or device are not touched.
- **Sign out**: Google Drive only. It ends Anvil's access to your Google account.
- **Delete**: destroy something: a file, folder, workspace, snippet, template or local history version.

**Writing style**
- Buttons and menu items use sentence case (**Save as**, **Try again**, **Clear recent files**). Only small section labels, such as LOCATIONS, are in capitals.
- Messages name the thing first and use the past tense: "notes.md saved", "Template “Report” deleted", "nas/share disconnected".

---

## 1. Introduction and Philosophy

Anvil is designed for software developers, system administrators, writers, and technical professionals who require a desktop-grade editor on Android and ChromeOS/Googlebook OS hardware.

### Core Principles

1. **Keyboard-First**: Every action, menu, dialog, and panel is fully accessible from physical and external keyboards without requiring touch input.
2. **Adaptive Layouts**: Rather than stretching a mobile UI or scaling down a desktop UI, Anvil adjusts its chrome, toolbars, and menus based on window dimensions and host environment (Phone, Tablet, Desktop / Samsung DeX / Googlebook OS).
3. **Data Integrity**: Atomic file saves, external modification detection, conflict resolution diffing, automated session recovery, local history snapshots, and strict memory safety caps (32 MB buffer limits).
4. **Zero Cloud Lock-in**: Direct local filesystem access, direct Linux VM host paths, and standard protocols such as SMB, with no proprietary cloud dependencies.

---

## 2. System Requirements and Installation

### System Requirements

- **Operating System**: Android 8.0 (API Level 26) or higher.
- **Form Factors**: Android Smartphones, Foldables, Tablets, Samsung DeX, Googlebook OS, Android Laptop, and ChromeOS (ARCVM).
- **Architecture**: Universal APK compatible with `arm64-v8a`, `armeabi-v7a`, `x86_64`, and `x86`.

### Installing on Android Phones and Tablets

1. Download the signed production package **`Anvil-release.apk`** from the official [Anvil Releases Repository](https://github.com/ccmscotland/Anvil-Releases/releases/latest).
2. Tap the downloaded file in your browser or file manager.
3. If prompted by Android, enable **Install unknown apps** for your browser or file manager.
4. Tap **Install** and launch Anvil.

### Installing on Googlebook OS and Android Laptop

1. Download `Anvil-release.apk` using Chrome.
2. Open the **Files** app, navigate to Downloads, and double-click `Anvil-release.apk` to install.
3. Alternatively, install via the Linux Terminal:
   ```bash
   adb install -r Anvil-release.apk
   ```

### Permissions Overview

- **Storage (Storage Access Framework / All Files)**: Used to open, edit, and persist files across internal storage, SD cards, and development folders (`/storage/emulated/10/Development`).
- **Internet**: Required for network storage (SMB, Google Drive), AI assistant queries, and MCP server network connections.
- **Microphone / Speech Recognition**: Used for voice typing and Rambler voice dictation fallback.

---

## 3. Adaptive Interfaces and Form Factors

Anvil monitors display metrics and system UI modes to present the optimal layout:

### Phone Shell (Width < 600 dp)
- **Top Bar**: Displays active document name, file path breadcrumb, quick save action, and overflow menu (`⋮`).
- **File Drawer**: Left slide-out drawer with a dismissible scrim. Open via swipe from the left edge or tap the menu button.
- **Bottom Toolbar**: Mobile quick buttons for high-frequency actions (`Undo`, `Redo`, `Find`, `Line`, `Cmds`, `Keys`).
- **Status Bar**: Compact footer showing cursor position (`Ln X, Col Y`), dirty state indicator (`•`), encoding, and storage provider.

### Tablet Shell (Width 600–1199 dp)
- **Persistent Drawer**: Fixed 220 dp sidebar displaying local folder trees, network locations, and workspaces.
- **Multi-Tab Strip**: Desktop-style tab strip across the top of the editor.
- **Split Editing**: Supports side-by-side dual-pane editing when rotated to landscape.

### Desktop, Samsung DeX, and Googlebook OS Shell (Width ≥ 1200 dp or Desktop UI Mode)
- **Full Menu Bar**: Complete desktop menus: `File`, `Find`, `Edit`, `Lines`, `Format`, `Tools`, `View`, `Documents`, `Help`.
- **Tab Strip with Middle-Click Close**: Close tabs with middle mouse click or the close button (`×`).
- **Draggable Side Panel**: Collapsible side panel hosting Document Symbols/Outline, Search in Files, and AI Assistant.
- **Native Multi-Window**: Press **`Ctrl+Alt+N`** (or `File -> New window`) to spawn independent editor instances.
- **Freeform Resizing**: Responsive window resizing down to 480 dp with fluid reflow.

> [!TIP]
> Press **`F11`** at any time to toggle **Zen Mode**, which hides menus, sidebars, tabs, and status bars for distraction-free writing. Press **`Esc`** or click the corner badge to return.

---

## 4. File Operations and Getting Started

### Creating and Opening Files
- **New File**: Press **`Ctrl+N`** to open a new blank untitled document.
- **New from Template**: Press **`Ctrl+Shift+N`** to create a file from built-in scaffolding (Python, Bash, Kotlin, HTML, Markdown, etc.).
- **Open File**: Press **`Ctrl+O`** to open the system Storage Access Framework (SAF) document picker.
- **Quick Open**: Press **`Ctrl+P`** to fuzzy-search across open tabs, recently opened files, and workspace trees.
- **Command Palette**: Press **`Ctrl+Shift+P`** or **`F1`** to search and trigger any editor action by name.

### Saving Files
- **Save**: Press **`Ctrl+S`** to write buffer changes to disk atomically.
- **Save As**: Press **`Ctrl+Shift+S`** to choose a new filename, storage location, or encoding.
- **Save All**: Select `File -> Save all` to persist all modified tabs at once.

### Auto-Save Modes
Configure auto-save behavior in `Settings -> Files & saving`:
- **Off** (default): Saves only when you ask. Files changed by other apps are never saved automatically.
- **After a pause**: Automatically saves 2 seconds after typing ceases.
- **On leaving Anvil**: Automatically writes modified buffers when switching to another application.

### External File Conflict Guard
If an open file is modified by an external process, Anvil detects the timestamp/size divergence and presents a safety prompt:
- **Reload from Disk**: Replaces the editor buffer with the external version (unsaved edits are safely archived in Local History).
- **Overwrite**: Forces the local editor buffer to disk.
- **Compare**: Opens a side-by-side line diff highlighting differences between buffer and disk.

### Local History
Anvil automatically takes snapshots of your documents during active editing sessions. Access past revisions via `File -> Local history…` to review timestamped diffs and roll back accidental deletions.

---

## 5. Document and Tab Management

- **Switching Tabs**:
  - Next Tab: **`Ctrl+Tab`**
  - Previous Tab: **`Ctrl+Shift+Tab`**
  - Direct Tab Jump: **`Ctrl+1`** through **`Ctrl+9`** (jumps directly to tabs 1 through 9)
- **Closing Tabs**: Press **`Ctrl+W`** (or middle-click the tab). Anvil prompts to save if the buffer has unsaved edits.
- **Reopen Closed Tab**: Press **`Ctrl+Shift+T`** to restore the most recently closed buffer.
- **Reordering Tabs**: Drag tabs horizontally with a mouse or touchpad, or press **`Ctrl+Shift+PageUp`** / **`Ctrl+Shift+PageDown`**. (`Ctrl+Shift+Left` / `Right` select word by word in the editor.)
- **In-Place Rename**: Double-click any active tab title or choose `File -> Rename…`.
- **Follow File (Live Tail)**: Press **`Ctrl+Alt+F`** (or `File -> Follow file`). Anvil continuously polls the file on disk and auto-scrolls to the end—ideal for live application and server logs.

---

## 6. Split Views and Live Previews

Anvil provides dual-pane workflows to maximize screen real estate on tablets, Chromebooks, and desktop monitors:

```
+-----------------------------------+-----------------------------------+
| Editor Pane 1 (Active)            | Editor Pane 2 / Live Preview      |
|                                   |                                   |
| def process_data(payload):        | ## Live Markdown / HTML Preview   |
|     parsed = json.loads(payload)  | Instant 250ms debounced updates   |
|     return parsed["results"]      | Offline sandboxed rendering       |
+-----------------------------------+-----------------------------------+
```

### Dual Document Split
- Press **`Ctrl+\`** (or `View -> Split view`) to toggle side-by-side editing.
- The active document occupies the left pane; selecting another tab assigns it to the right pane.
- Click into either pane to transfer editing focus.

### Live Markdown and HTML Preview
- Press **`Ctrl+Shift+\`** (or `View -> Preview beside the editor`) to open the live preview pane beside the editor.
- Updates automatically 250 ms after typing stops.
- Security-hardened: Renders in an offline sandbox with no script execution or external network calls.
- Supports CommonMark, GitHub-style alerts (`[!NOTE]`, `[!TIP]`, `[!WARNING]`, `[!IMPORTANT]`, `[!CAUTION]`), task lists (`- [x]`), tables, and sanitized HTML tags (`<kbd>`, `<sub>`, `<sup>`, `<details>`).

---

## 7. Editing, Navigation and Cursor Superpowers

### Navigation and Cursor Movement
- **Go to Line**: Press **`Ctrl+G`**, type a line number (or `line:column`, or `+n` / `-n` to move relative to the caret), and press Enter.
- **Go to Symbol Outline**: Press **`Ctrl+R`** to view a quick outline of functions, classes, markdown headings, and tags in the document.
- **Matching Brackets**: Press **`Ctrl+Shift+M`** to jump between matching `()`, `{}`, and `[]`. Press **`Ctrl+Shift+]`** to select the enclosed block.
- **Word Wrap**: Press **`Alt+Z`** to toggle line wrapping.

### Multi-Cursor and Column Editing
- **Stacked Carets**: Press **`Ctrl+Alt+Up`** or **`Ctrl+Alt+Down`** to add additional cursors on adjacent lines.
- **Select Next Occurrence**: Press **`Ctrl+D`** (or `Edit -> Add next occurrence`) to select the next matching word with a new caret.
- **Select All Occurrences**: Select `Edit -> Select all occurrences` to edit every instance across the document simultaneously.
- **Column / Box Selection**: Select a block of text and choose `Edit -> Column selection` to transform the selection into a vertical rectangular edit block.

### Line Operations
- **Duplicate Line**: Press **`Ctrl+D`** with no active selection to duplicate the current line.
- **Delete Line**: Press **`Ctrl+Shift+K`** to delete the line under the cursor.
- **Move Lines**: Press **`Alt+Up`** or **`Alt+Down`** to shift lines up or down.
- **Join Lines**: Select `Lines -> Join lines` (**`Ctrl+J`**) to collapse selected lines into a single line.
- **Sort and Deduplicate**: Use `Lines -> Sort lines A to Z`, `Sort lines Z to A`, and `Remove duplicate lines`.
- **Line Bookmarks**: Press **`Ctrl+F2`** to toggle a bookmark on the current line; press **`F2`** / **`Shift+F2`** to cycle forward and backward.

### Find and Replace
- **In-Buffer Search**: Press **`Ctrl+F`** to open the search bar. Supports Case Sensitivity (`Aa`), Whole Word (`\b`), and Regular Expressions (`.*`) with `$1`, `$2` replacement groups. Press `Enter` or `F3` for next match; `Shift+F3` for previous match.
- **Search in Files**: Press **`Ctrl+Shift+F`** to search across an entire project folder or workspace, complete with replacement previews and undo rollback.

---

## 8. Googlebook OS Rambler and Voice Dictation

Anvil includes dedicated integration with Googlebook OS Gemini-powered **Rambler** voice dictation and Gboard voice typing.

### Hardware and Keyboard Shortcuts
- **Dedicated Dictation Key**: Tap the hardware dictation key (`KEYCODE_DICTATE` = 319) on compatible laptop keyboards to activate voice typing immediately.
- **System Dictation Shortcuts**: Press **`Alt+D`** or **`Search+D`** (`Meta+D`) to invoke system voice typing.
- **Command Palette & Menus**: Trigger `Edit -> Voice dictation (Rambler)…` or search for `dictate` in the Command Palette (`Ctrl+Shift+P`).

### Context-Aware Thought-to-Text
Anvil provides continuous multi-line input connections (`InputType.TYPE_CLASS_TEXT or InputType.TYPE_TEXT_FLAG_MULTI_LINE`) and populates surrounding context (`EditorInfoCompat.setInitialSurroundingText`). This allows Gemini:
- To understand the sentences preceding and following the cursor.
- To execute context-aware thought-to-text rewrites and grammar corrections without truncating adjacent code or punctuation.
- To keep the cursor selection synchronized in real time via `InputMethodManager.updateSelection`.

---

## 9. Touchpad, Mouse and Laptop Gestures

- **Two-Finger Touchpad Scrolling**: Smooth momentum scrolling vertically and horizontally across large files.
- **Font Zoom Gestures**:
  - Hold **`Ctrl`** and roll the mouse scroll wheel or pinch the touchpad to smoothly scale editor text from 70% to 250%.
  - Press **`Ctrl+0`** to reset zoom back to 100%.
- **Drag and Drop**: Drag files from the Googlebook OS / Android Files app directly onto the editor window to open them in new tabs. Text dragged onto the editor is inserted where you drop it; text dropped elsewhere in the window opens as a new document. Images and other non-text files are refused.

---

## 10. Languages, Grammars and Code Intelligence

Anvil bundles syntax highlighters and language grammars for **over 30 languages** powered by TextMate grammars and Sora Editor:

| Category | Languages |
|---|---|
| **Scripting and Web** | Python, JavaScript, TypeScript, HTML, CSS, PHP, Ruby, Perl, Lua |
| **Compiled and Systems** | Kotlin, Java, C, C++, C#, Go, Rust, Swift |
| **Shell and DevOps** | Bash/Shell, PowerShell, Dockerfile, Makefile, Diff/Patch |
| **Data and Markup** | Markdown, JSON, YAML, XML, SQL, INI, TOML, `.editorconfig`, Nginx |

### Automatic Language Detection
When opening extensionless files (such as scripts, dotfiles, or `/etc/` configurations), Anvil automatically identifies the syntax through:
1. Shebang headers (`#!/usr/bin/env python3`, `#!/bin/bash`, etc.).
2. Structured openers (`<?xml`, `<!DOCTYPE html>`, `{ "key": ... }`).
3. Characteristic language signatures (`fun main()`, `def __init__`, `SELECT * FROM`).

---

## 11. Snippets and New-File Templates

### Snippets
Anvil bundles **over 300 built-in snippets** covering common idioms, structures, and control flow for every supported language:
- **Tab Expansion**: Type a trigger word (e.g., `def`, `class`, `for`, `try`, `table`, `strict`) and press **`Tab`**.
- **Snippet Picker**: Press **`Ctrl+E`** (or `Edit -> Insert snippet…`) to browse snippets for the active language.
- **Dynamic Variables**: Automatically resolves `$DATE`, `$TIME`, `$YEAR`, and `$FILENAME`.
- **Caret Stops**: Tab cycles between `${1:placeholder}` stops and lands at `$0`.

### New from Template
Press **`Ctrl+Shift+N`** (or `File -> New from template…`) to scaffold a new file:
- **Built-in Templates**: Shell script (`script.sh`), Python script (`script.py`), Kotlin file (`Main.kt`), HTML5 page (`index.html`), Markdown note (`note.md`), `.editorconfig`, Dockerfile, Makefile, JSON, and YAML.
- **Custom Templates**: Open any document and select `File -> Save as template…` to turn it into a reusable template.

---

## 12. Built-in Text Tools and Transforms

Located under `Tools` or the Command Palette, Anvil provides zero-dependency text utilities:

- **Format JSON**: Pretty-prints JSON with consistent indentation.
- **Minify JSON**: Compresses JSON payloads into a single dense string.
- **Format XML**: Cleans and indents XML/HTML tags and attributes.
- **Base64 Encode / Decode**: Standard UTF-8 Base64 conversions.
- **URL Encode / Decode**: Percent-encoding for URLs and query parameters.
- **Hashes Dialog**: Computes MD5, SHA-1, and SHA-256 hashes with one-tap clipboard copy.

> [!NOTE]
> All tools adhere to the **Selection Rule**: If text is selected, the tool transforms only that selection; if nothing is selected, it transforms the entire document.

---

## 13. Storage Locations and Remote Connections

Anvil connects directly to local filesystems and remote servers without third-party sync utilities:

Every place you browse is a **location**. Add one from the drawer or `File -> Add a location…`, and rename, reorder or remove them in `File -> Manage locations…`.

- **Device folder**: any folder you grant Anvil access to through the system folder picker.
- **Network share (SMB)**: an SMB2 or SMB3 share on a PC, Mac or NAS, with optional domain sign-in. SMB1-only servers aren't supported.
- **Google Drive**: browse, open and save directly to your Google Drive account. Use **Sign out** in its ⋮ menu to end access.

Each server location's ⋮ menu offers **Edit connection…**, **Disconnect** (keeps its settings) and **Remove…** (takes it off Locations and deletes its saved password or token from this device).

---

## 14. AI Assistant Integration

Anvil includes a built-in AI assistant dialog (`Ctrl+Shift+A` or `Edit -> Ask AI…`):

- **Supported Providers**:
  - **Google Gemini** (default: `gemini-2.5-flash`)
  - **Anthropic Claude** (default: `claude-sonnet-5`)
  - **OpenAI** (default: `gpt-4o-mini`)
- **Context Scope**: Send selected text, the whole document (safely capped at 60k characters), or prompt-only.
- **Quick Prompts**: `Explain`, `Fix`, `Improve`, `Summarise`, or custom instructions.
- **Actions**: `Insert at caret`, `Replace selection`, or `Copy to clipboard`.
- **Security**: API keys are encrypted in Android Keystore (AES-GCM) and only transmitted in request headers directly to the provider.

---

## 15. Theming, Typography and Appearance

Customize the editor in `Settings -> Appearance` or `View -> Font & size…` (**`Ctrl+Shift+O`**):

### 10 Color Themes
- **Light**: Paper (default), GitHub Light, Solarized Light.
- **Dark**: Ink (default), Nord, Dracula, Monokai, Gruvbox Dark, One Dark, Solarized Dark.
- *Quick Toggle*: Press **`Ctrl+Shift+D`** to switch between Paper and Ink instantly. All themes pass WCAG AA contrast standards.

### 7 Monospace Fonts
- **IBM Plex Mono** (default)
- **JetBrains Mono**
- **Fira Code**
- **Source Code Pro**
- **Ubuntu Mono**
- **Inconsolata**
- **System Monospace**

---

## 16. Settings, Keymap and EditorConfig

### Settings Sheet
Access settings via `Help -> Settings` or the Command Palette (`Ctrl+Shift+P`):
- Tab width (2, 4, 8 spaces, or Tabs).
- Default line endings (LF, CRLF, CR).
- Fallback encoding for non-UTF-8 files (34 supported encodings).
- Bracket auto-close and step-over.

### `.editorconfig` Support
Anvil traverses parent directories for `.editorconfig` files and automatically applies:
- `indent_style` and `indent_size`.
- `end_of_line` (`lf`, `crlf`, `cr`).
- `trim_trailing_whitespace` and `insert_final_newline` on save.

### Custom Keyboard Shortcuts
In `Settings -> Keyboard shortcuts`, you can rebind any command:
1. Tap or select the command row.
2. Press your preferred key combination.
3. Anvil validates conflicts and rebinds cleanly.

---

## 17. Model Context Protocol (MCP) Integration

Anvil features a built-in MCP server (`mcp/`) that lets AI agents (such as Antigravity, Claude Desktop, Cursor, and Zed) inspect and automate editor workflows:

- **Documentation**: Search, read, outline, create, and update project docs.
- **Editor Intelligence**: Query snippet bodies, render templates, detect languages, and format text.
- **Testing and Builds**: Run Gradle JVM unit tests (`anvil_run_tests`) and trigger APK builds (`anvil_build_apk`).
- **Live Bridge**: Open files directly inside Anvil via `anvil_open_in_editor`.
- **Transports**: Standard `stdio` (local desktop tools) and HTTP/Server-Sent Events (`sse`) with Bearer token authentication (for remote web clients and Claude Android Custom Connectors).

See `mcp/anvil-docs-mcp/README.md` for complete configuration instructions.

---

## 18. Comprehensive Keyboard Shortcuts Reference

| Shortcut | Command / Action | Menu Location |
|---|---|---|
| **`Ctrl+N`** | New blank document | `File -> New file` |
| **`Ctrl+Alt+N`** | New editor window | `File -> New window` |
| **`Ctrl+Shift+N`** | New file from template | `File -> New from template…` |
| **`Ctrl+O`** | Open file from storage | `File -> Open file…` |
| **`Ctrl+S`** | Save active document | `File -> Save` |
| **`Ctrl+Shift+S`** | Save As new file/path | `File -> Save as…` |
| **`Ctrl+W`** | Close current tab | `File -> Close tab` |
| **`Ctrl+Shift+T`** | Reopen last closed tab | `File -> Reopen closed tab` |
| **`Ctrl+Tab`** | Next tab | Tab Strip |
| **`Ctrl+Shift+Tab`** | Previous tab | Tab Strip |
| **`Ctrl+1`..`Ctrl+9`** | Jump to tab 1..9 | Tab Strip |
| **`Ctrl+\`** | Toggle dual-document split | `View -> Split view` |
| **`Ctrl+Shift+\`** | Toggle live preview split | `View -> Preview beside editor` |
| **`Ctrl+P`** | Quick open / jump to file | `Find -> Quick open by name…` |
| **`Ctrl+Shift+P`** / **`F1`** | Open Command Palette | Palette Button / `Help` |
| **`Ctrl+F`** | Find and Replace in buffer | `Find -> Find & replace` |
| **`Ctrl+Shift+F`** | Search across folder/files | `Find -> Search in files…` |
| **`Ctrl+G`** | Go to line number | `Find -> Go to line` |
| **`Ctrl+R`** | Go to symbol / outline | `Find -> Go to symbol` |
| **`Ctrl+E`** | Insert code snippet | `Edit -> Insert snippet` |
| **`Ctrl+Shift+A`** | Ask AI assistant | `Edit -> Ask AI…` |
| **`Alt+D`** / **`Search+D`** | Voice dictation (Rambler) | `Edit -> Voice dictation…` |
| **`Ctrl+D`** | Duplicate line / Add next cursor | `Lines -> Duplicate line` |
| **`Ctrl+Shift+K`** | Delete current line | `Lines -> Delete lines` |
| **`Alt+Up` / `Down`** | Move lines up / down | `Lines -> Move lines up/down` |
| **`Ctrl+Alt+Up` / `Down`** | Add stacked cursor above / below | `Edit -> Add cursor above/below` |
| **`Ctrl+Shift+M`** | Jump to matching bracket | `Edit -> Jump to bracket` |
| **`Ctrl+/`** | Toggle line comment | `Edit -> Toggle line comment` |
| **`Ctrl+L`** | Select line (again to extend) | `Edit -> Select line` |
| **`Ctrl+]`** / **`Ctrl+[`** | Indent / outdent lines | `Lines -> Indent / Outdent lines` |
| **`Ctrl+Enter`** | Insert line below | `Lines -> Insert line below` |
| **`Shift+Alt+Down`** | Copy line down | `Lines -> Copy line down` |
| **`F3`** / **`Shift+F3`** | Find next / previous | `Find -> Find next/previous` |
| **`Ctrl+Shift+/`** | Keyboard shortcuts sheet | `Help -> Keyboard shortcuts` |
| **`Ctrl+Shift+]`** | Select enclosed bracket block | `Edit -> Select enclosing block` |
| **`Ctrl+F2`** | Toggle line bookmark | Gutter / `Edit -> Toggle bookmark` |
| **`F2`** / **`Shift+F2`** | Next / Previous bookmark | `Edit -> Next/Prev bookmark` |
| **`Alt+Z`** | Toggle word wrap | `View -> Word wrap` |
| **`Ctrl+Shift+O`** | Font and font size overlay | `View -> Font & size…` |
| **`Ctrl+Shift+D`** | Quick toggle Dark/Light theme | `View -> Dark editor` |
| **`Ctrl+=` / `Ctrl+-`** | Zoom in / Zoom out editor | `View -> Zoom in/out` |
| **`Ctrl+0`** | Reset editor zoom | `View -> Reset zoom` |
| **`F11`** | Toggle Zen Mode (fullscreen) | `View -> Zen mode` |
| **`Ctrl+Alt+F`** | Follow file (`tail -f`) | `File -> Follow file` |

---

## 19. Troubleshooting and FAQ

### Q: Why does the app say "Open a document first"?
**A**: Commands that modify text (such as Find, Snippets, or Format tools) require an active document buffer. Open or create a file with `Ctrl+N` or `Ctrl+O`.

### Q: How do I open files directly from the Linux Terminal on Googlebook OS?
**A**: Anvil can open files directly from the command line:
```bash
adb shell am start -a android.intent.action.VIEW -d "file:///storage/emulated/10/Development/Anvil/README.md" -t "text/plain"
```

### Q: How do I resolve permission errors when opening local folders?
**A**: Ensure Anvil has been granted Storage access. For development folders, navigate to `File -> Add a location…` and select your local development directory using the system folder picker.

### Q: Where are unsaved crash snapshots stored?
**A**: Anvil persists temporary recovery sessions in the application cache. If an abnormal shutdown occurs, Anvil automatically detects the recovery manifest on subsequent startup and offers to restore open buffers.
