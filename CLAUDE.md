# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an **Obsidian Plugin** written in TypeScript that serves as the official sample/template for Obsidian plugin development. It demonstrates core plugin API capabilities including UI elements, commands, settings, and event handling.

## Development Commands

```bash
# Install dependencies
pnpm i

# Development with watch mode (auto-rebuilds on changes)
pnpm run dev

# Production build with type checking
pnpm run build

# Version bumping (updates manifest.json, package.json, versions.json)
pnpm version patch|minor|major

# Code linting
eslint main.ts
```

## Development Workflow

1. **Local Development**: Clone to `.obsidian/plugins/your-plugin-name/` in an Obsidian vault
2. **Build Process**: ESBuild bundles `main.ts` → `main.js` with source maps for debugging
3. **Testing**: Reload Obsidian after changes, enable plugin in settings
4. **Node.js Requirement**: Minimum v16

## Code Quality

- Follow rules defined in .editorconfig

## Architecture

### Plugin Structure (`main.ts`)

- **MyPlugin**: Main plugin class extending Obsidian's Plugin base class
- **SampleModal**: Modal dialog implementation
- **SampleSettingTab**: Settings interface implementation

### Key Plugin Capabilities Demonstrated

- **UI Elements**: Ribbon icons, status bar items, modal dialogs
- **Commands**: Simple commands, editor commands with selection handling, conditional commands with check callbacks
- **Settings**: Plugin settings tab with persistent storage via `loadData()`/`saveData()`
- **Event Handling**: Global DOM events via `registerDomEvent()`, intervals via `registerInterval()`
- **Lifecycle**: `onload()` for initialization, `onunload()` for cleanup

### Configuration Files

- **manifest.json**: Plugin metadata (id, version, minAppVersion, cross-platform support)
- **versions.json**: Obsidian compatibility matrix for different plugin versions
- **tsconfig.json**: TypeScript config targeting ES6 with strict null checks

## Release Process

1. Update version in `manifest.json` and `minAppVersion` if needed
2. Update `versions.json` compatibility matrix
3. Create GitHub release with exact version number (no `v` prefix)
4. Upload `manifest.json`, `main.js`, `styles.css` as release assets
5. Use `npm version` commands to automate version bumping across files

## API References

- Main API: https://github.com/obsidianmd/obsidian-api
- Plugin Guidelines: https://docs.obsidian.md/Plugins/Releasing/Plugin+guidelines
- Community Plugin Submission: https://github.com/obsidianmd/obsidian-releases
