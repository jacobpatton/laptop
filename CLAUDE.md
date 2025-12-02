# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a macOS laptop setup script that automates development environment configuration. The main `mac` script is idempotent and can be run multiple times safely.

## Running the Script

```bash
# Run the setup script (interactive prompts for Web/iOS/Android dependencies)
bash mac 2>&1 | tee ~/laptop.log
```

## Linting

```bash
# Install ShellCheck for shell script linting
brew install shellcheck

# Run ShellCheck on the main script
shellcheck mac
```

## Architecture

The codebase consists of a single Bash script (`mac`) with the following structure:

- **Helper functions**: `fancy_echo`, `append_to_zshrc`, `prepend_to_zshrc`, `gem_install_or_update`
- **Installation functions**: `install_homebrew`, `install_asdf`, `install_dependencies`
- **Dependency configuration**: `append_*_dependencies` functions build a Brewfile at `~/.Brewfile`
- **asdf language installers**: `install_asdf_*` functions for Ruby, Node.js, Erlang, Elixir, Go

The script supports both Apple Silicon (arm64) and Intel architectures, with `HOMEBREW_PREFIX` set accordingly.

## Key Customization Points

- User customizations go in `~/.laptop.local` (sourced at the end of the script)
- The script uses Homebrew Bundle with a global Brewfile at `~/.Brewfile`
- Functions like `brew`, `cask`, `fancy_echo`, and `gem_install_or_update` are available in `~/.laptop.local`

## Shell Script Guidelines

- Follow [ShellCheck](https://www.shellcheck.net/) recommendations
- Use `set -e` for strict error handling
- Use `trap` for cleanup on failure
- Write idempotent code that can run multiple times safely
