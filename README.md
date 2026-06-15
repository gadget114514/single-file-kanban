# Single File Kanban Board

A single-file Kanban board viewer/editor that runs entirely in the browser. No server, no build step, no dependencies.

![Kanban Board](https://img.shields.io/badge/version-1.0.0-blue) ![License](https://img.shields.io/badge/license-MIT-green)

## Features

- **Zero dependencies** - Pure HTML/CSS/JavaScript in a single file
- **Offline capable** - Works without internet connection
- **File-based** - Data stored in plain JSON, easy to version control with Git
- **Drag & drop** - Move cards between columns intuitively
- **Auto-save** - Changes are saved automatically (400ms debounce)
- **Bilingual** - Japanese and English UI
- **Responsive** - Horizontal scrolling for many columns

## Quick Start

1. Open `kanban.html` in Chrome or Edge
2. Copy `kanban.template.json` to `kanban.json`
3. Drag `kanban.json` onto the "Open file" button (or click to browse)
4. Click "Edit" to enable editing mode

That's it! No installation required.

## Usage

### View Mode

- **Click a card** to toggle done/undone status
- **Priority colors** - Left border indicates priority: 🔴 High, 🟡 Medium, 🟢 Low, ⚪ None
- **Overdue cards** - Displayed with red background and ⚠ icon
- **Done cards** - Displayed with strikethrough and green background

### Edit Mode

Click the **Edit** button (turns green) to enable editing:

**Cards:**
- Click **+ Add card** at the bottom of each column
- Click ✎ on a card to edit (title, description, assignee, priority, due date, tags)
- Click ✕ to delete a card
- Drag cards between columns, or use ◀ ▶ buttons

**Columns:**
- Click **+ Add column** to create a new column
- Click ✎ on column header to edit name and color
- Drag column headers to reorder, or use ◀ ▶ buttons

### Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Ctrl+S` | Save immediately (edit mode only) |
| `Esc` | Close modal dialog |

## JSON Format

The data file (`kanban.json`) uses this structure:

```json
{
  "board": "Project Name",
  "columns": [
    {
      "id": "column-id",
      "name": "Column Name",
      "color": "#6366f1",
      "cards": [
        {
          "id": "card-id",
          "title": "Card Title",
          "description": "Description text (URLs auto-linkified)",
          "assignee": "Assignee Name",
          "priority": "high",
          "dueDate": "2026-07-01",
          "tags": ["tag1", "tag2"],
          "done": false
        }
      ]
    }
  ]
}
```

### Required Fields

| Field | Location | Description |
|-------|----------|-------------|
| `columns` | root | Array of columns |
| `name` | column | Column name |
| `title` | card | Card title |

All other fields are optional. IDs are auto-generated if omitted.

### Priority Values

- `"high"` - Red left border
- `"medium"` - Yellow left border
- `"low"` - Green left border
- `"none"` - Gray left border (default)

## File Structure

```
├── kanban.html           # Main application (single file)
├── kanban.json           # Your data file (create from template)
├── kanban.template.json  # Empty template to get started
├── kanban_guide.html     # User guide (Japanese)
└── README.md             # This file
```

## Browser Compatibility

| Browser | View | Edit |
|---------|------|------|
| Chrome / Edge | ✅ | ✅ |
| Firefox | ✅ | ⚠️ (no auto-save) |
| Safari | ✅ | ⚠️ (no auto-save) |

Edit mode uses the [File System Access API](https://developer.mozilla.org/en-US/docs/Web/API/File_System_Access_API), which is only supported in Chromium-based browsers.

## Tips

- **Backup your data** - `kanban.json` is plain JSON, so you can commit it to Git or copy it manually
- **URL auto-linking** - URLs in card descriptions (starting with `http://` or `https://`) become clickable links
- **External changes** - If `kanban.json` is modified by another tool, you'll be prompted before overwriting
- **Language setting** - UI language preference is saved in browser localStorage

## License

MIT License - see [LICENSE](LICENSE) file for details.

## Related Projects

This Kanban board follows the same single-file architecture as single-file-wbs, a Gantt chart viewer for Work Breakdown Structure data.
