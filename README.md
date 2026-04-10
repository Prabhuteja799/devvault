# DevVault

A zero-dependency personal knowledge base for developers. Write and organize notes in Markdown with nested folders, syntax-highlighted code blocks, complexity tags, and drag-and-drop reordering — all stored in your browser's `localStorage`. No account, no server, no setup.

**Live:** [prabhuteja799.github.io/devvault](https://prabhuteja799.github.io/devvault/)

---

## What it does

DevVault is a single HTML file that works as a full-featured developer notebook. Notes are written in a structured Markdown format and rendered instantly. Everything lives in `localStorage` — close the tab, reopen it, your notes are still there.

It's designed for storing things like:
- Algorithm and data structure notes with working code examples
- System design concepts
- Interview prep notes with time/space complexity
- Anything you'd otherwise scatter across random `.md` files

---

## Features

### Notes
- Write notes in **structured Markdown** — headings, bullets, numbered lists, blockquotes, bold, italic, inline code, horizontal rules
- **Editable sections** — click any rendered section to edit it in-place; no separate edit mode
- **Code blocks** — fenced ` ``` ` blocks with a click-to-edit inline editor
- **Copy button** on every code block
- **Images** — paste or embed images directly into notes
- **Auto-tagging** — note content is scanned for known algorithm tags (HashMap, Two Pointers, Sliding Window, Binary Search, Dynamic Programming, BFS, DFS, Sorting, Greedy, Trees, Graphs, etc.) and shown as chips on the card
- **Complexity detection** — `Time complexity: O(n)` and `Space complexity: O(1)` are parsed from note text and displayed on the card

### Folders
- **Unlimited nesting** — create folders inside folders to any depth
- **Expand / collapse** any folder in the sidebar tree
- **Rename / delete** folders via right-click context menu
- **Drag and drop** — drag notes or folders onto other folders to reorganize
- **Move to folder** modal — keyboard-navigable folder picker with search (⌘M or context menu)
- **Drop indicator line** — shows where an item will land while dragging

### Search
- **Global search** across all note titles and content
- Highlights matching notes in the tree

### UI
- **Dark / light mode** — manual toggle + respects `prefers-color-scheme` system preference
- **Syntax highlighting** — Java, Python, JavaScript, SQL, and more (VS Code / GitHub Dark inspired color tokens)
- **JetBrains Mono** for all code, Inter for UI
- Smooth transitions, layered depth surfaces in dark mode, clean flat surfaces in light mode
- Custom scrollbars, hover states, animated modals

### Data
- **100% localStorage** — no server, no account, no sync
- **Export** — download all notes as a JSON backup
- **Import** — restore from a previously exported JSON file

---

## How notes are written

Notes use a simple Markdown-like format:

```markdown
# Note Title

## Section Heading

Regular paragraph text with **bold**, *italic*, and `inline code`.

- Bullet item
- Another bullet

1. Numbered item
2. Second item

> Blockquote for callouts or quotes

Time complexity: O(n log n)
Space complexity: O(n)

```java
public int binarySearch(int[] arr, int target) {
    int lo = 0, hi = arr.length - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}
```
```

Each `## Heading` becomes a collapsible section in the rendered view. Code blocks get a language label, copy button, and click-to-edit inline editor.

---

## Keyboard shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl/⌘ + N` | New note |
| `Ctrl/⌘ + Shift + N` | New folder |
| `Ctrl/⌘ + S` | Save current note |
| `Ctrl/⌘ + M` | Move selected item to folder |
| `Escape` | Close modal / cancel |
| `Enter` | Confirm modal / move |
| `↑ / ↓` | Navigate folder list in Move modal |

---

## Running locally

It's a single file — just open it:

```bash
open index.html
```

Or serve it:

```bash
npx serve .
# http://localhost:3000
```

No `npm install`. No build step. No config.

---

## Deploying to GitHub Pages

1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to `main` branch, root `/`
4. Your vault is live at `https://<username>.github.io/devvault/`

Your notes stay in **your own browser's localStorage** — they are never sent anywhere.

---

## Tech

| Concern | How |
|---|---|
| Rendering | Vanilla JS custom Markdown parser |
| Syntax highlight | Custom tokenizer (Java, Python, JS, SQL) |
| Storage | `localStorage` JSON |
| Fonts | Google Fonts — Inter + JetBrains Mono |
| Styling | CSS custom properties (design tokens) |
| Framework | None — single HTML file, zero dependencies |
