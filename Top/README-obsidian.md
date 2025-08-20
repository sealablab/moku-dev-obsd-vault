# Obsidian Configuration Notes

## Overview
This directory serves as the functional "top level" for Obsidian vault operations within the knowledge base.

## Configuration Tricks

### Trash Location
- **Current setting**: `"trashOption": "local"`
- **Behavior**: Creates `.trash/` folder in main workspace root (not ideal)
- **Why**: Obsidian doesn't allow custom trash folder paths
- **Acceptance**: Living with this minor inconsistency for now

### Git Tracking Strategy
- **`.obsidian/` files tracked**: Core settings, plugins, appearance, hotkeys
- **`.obsidian/workspace.json` excluded**: Personal workspace layout (changes constantly)
- **`.trash/` excluded**: Main workspace gitignore (since we can't control location)

### File Organization
- **`Top/` directory**: Your Obsidian workspace - anything goes here
- **External linking**: Can still link to files anywhere in the structure
- **Flexible evolution**: Let organization settle over time

## Key Settings
```json
{
  "trashOption": "local",           // Local trash (creates .trash/ in main workspace)
  "alwaysUpdateLinks": true,        // Keeps links working when files move
  "newFileLocation": "current",     // Creates files where you are
  "newLinkFormat": "relative",      // Relative links for better portability
  "showUnsupportedFiles": true,     // Shows all file types
  "attachmentFolderPath": "./",     // Attachments in current folder
  "promptDelete": false             // No delete prompts
}
```

## Notes
- Obsidian sync is working well with this setup
- File deletions go to main workspace `.trash/` (minor inconvenience)
- Core configuration is version controlled for team consistency
- Personal workspace preferences stay local
