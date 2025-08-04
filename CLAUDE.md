# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A command-line tool (ccx) for managing and switching between different API providers for Claude Code.

## Development Commands

```bash
# Install dependencies
npm install

# Development mode
npm run dev          # Run with ts-node
npm run build        # Compile TypeScript
npm start            # Run compiled version
npm test             # Run tests
npm run lint         # Run ESLint
npm run pkg          # Create cross-platform executables
```

## Core CLI Commands

```bash
# After building or running dev mode
ccx list             # List all API providers
ccx current          # Show current provider
ccx use <provider>   # Switch provider
ccx add <provider>   # Add new provider
ccx remove <provider> # Remove provider
ccx test [provider]  # Test API connection
ccx config           # Open config file
```

## Project Architecture

### Key Components

- `src/cli/`: CLI command implementations
  - `list.ts`: List providers
  - `current.ts`: Show current provider
  - `use.ts`: Switch provider
  - `add.ts`: Add provider
  - `remove.ts`: Remove provider
  - `test.ts`: Connection testing
  - `config.ts`: Configuration management

- `src/utils/`: Utility functions
  - `config.ts`: Configuration management
  - `api.ts`: API testing utilities

### Key Dependencies

- **Runtime**: commander, chalk, inquirer, axios, fs-extra, json5
- **Development**: typescript, ts-node, jest, eslint, pkg

## Configuration Management

### Config Files

- `~/.claude/providers.json`: Provider configurations
- `~/.claude/settings.json`: Active provider settings
- `package.json`: Project metadata

### Provider Configuration Example

```json
{
  "current": "anthropic",
  "providers": {
    "anthropic": {
      "name": "Anthropic",
      "api_key": "sk-...",
      "base_url": "https://api.anthropic.com",
      "model": "claude-3-5-sonnet-20241022"
    }
  }
}
```

## Development Workflow

### Adding Features

1. Implement command handler in `src/cli/`
2. Export from `src/index.ts`
3. Add TypeScript types
4. Test with `npm run dev`
5. Update documentation

### Deployment

```bash
npm run build        # Compile TypeScript
npm run pkg          # Create cross-platform executables
```

## Important Considerations

- Modifies `~/.claude/settings.json` to switch providers
- API keys stored in plain text configuration
- Always test API connections before switching
- Automatic backup created before config changes