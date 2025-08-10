# CLAUDE.md - Tools Project

This project tracks tools on the machine using CSV files. It includes both tools actively used and tools tracked for potential future installation.

## Files

- `tools.csv` - Public list of tools (tracked by git)
- `tools-private.csv` - Private list of tools (ignored by git)

## CSV Columns

| Column | Description |
|--------|-------------|
| name | Tool name (unique identifier) |
| category | Tool category |
| official_link | Official website or repository |
| install_method | How the tool was installed (yay, pacman, npm, cargo, etc.) |
| description | Brief description of the tool |
| comment | Personal notes or configuration reminders |
| install_date | Date when the tool was installed (YYYY-MM-DD) |

## Commit Format

Use conventional commit style with the tool name as scope (kebab-case):

```
add(tool-name): fun one-liner
remove(tool-name): fun one-liner
update(tool-name): fun one-liner
```

### Commit Message Style

The commit message should be a **fun one-liner** - NOT the tool description. Be creative:
- A joke or witty remark
- Personal context or justification
- A reference to why you needed it
- Something memorable and human

**Examples:**
- `add(1password): Tried a paper notebook, wasn't a great idea`
- `add(fzf): So fast!!!`
- `add(bun): Everyone keeps talking about it, had to try`
- `add(lazygit): Because typing git commands is so 2010`
- `add(bat): cat but make it fancy`
- `remove(node): Bun took over, sorry old friend`

## Operations

### Adding a tool

1. If install method is not specified, ask the user
2. Search online for: official link, description
3. Reuse an existing category if relevant
4. Set `install_date` to the current date automatically
5. **Package naming convention:** Use the generic tool name in the `name` column (e.g., "bun"). If the actual installed package has a different name (e.g., "bun-bin"), put it in the `comment` column with format: `installed via {install_method} as {package_name}`
   - Example: `name: bun`, `install_method: yay`, `comment: installed via yay as bun-bin`
6. Tools are **public by default** (add to `tools.csv`)
7. If the user mentions "private" or "hidden", add to `tools-private.csv` instead

### Removing a tool

- **Default behavior:** Delete the row from the CSV
- **If specified "not installed":** Keep the row but set `install_method=not installed` and clear `install_date`

### Updating a tool

- Modify only the requested fields

### Searching for a tool

1. First search in existing CSV files (`tools.csv` and `tools-private.csv`)
2. If not found, suggest alternatives via web search

## Auto-commit and push

On every modification:
1. Commit with the appropriate format
2. Push to remote automatically

## Existing Categories

Reuse these categories when possible:

- AI Tools
- Communication
- Development
- File Management
- File Sync & Download
- GNOME
- Media
- Networking & Security
- Shell & Terminal
- System & Core
- Text & Data Processing
- Utilities
- Web Browser
