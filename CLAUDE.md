# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Scope is a Rust-based "System for Contextual Orchestration of Projects & Execution" that provides intelligent project management, execution workflows, and context-aware automation using a three-crate workspace architecture.

### Core Architecture

1. **scope-core** - Core functionality, orchestration engine, and shared libraries
2. **scope-cli** - Command-line interface for system interaction  
3. **scope-web** - Web interface for project management and workflows

### Critical Rules

- Target Rust 1.70+ with 2021 edition
- All crates inherit workspace package metadata (version, authors, license, etc.)
- Use workspace dependencies for consistency: `tokio`, `serde`, `clap`
- Both CLI and web interfaces depend on scope-core for shared functionality
- Use `scope-` prefix for all new crates

**File Size Limits:**
- Code files: Maximum 300 lines - decompose into components if necessary
- Documentation files: Maximum 500 lines - separate by topic with index references
- Memory files: Maximum 100 lines - use index reference pattern

## Memory Files Reference

- **Commands & Development**: See `memory/commands.md` for Cargo commands, build, test, and development workflows
- **Architecture Details**: See `memory/architecture.md` for workspace structure, crate relationships, and design principles
- **Development Workflow**: See `memory/development.md` for setup, best practices, and common development tasks
- **Dependencies Management**: See `memory/dependencies.md` for workspace dependencies and version management
- **Crate Creation**: See `memory/crate-creation.md` for adding new crates to the workspace
- **File Size Guidelines**: See `memory/file-size-guidelines.md` for file size limits and decomposition strategies
- **Documentation Guidelines**: See `memory/documentation-guidelines.md` for project documentation standards and organization
- **Rust Documentation Standards**: See `memory/rust-documentation-standards.md` for Rust code documentation patterns and JSDoc-equivalent practices
- **README Maintenance**: See `memory/readme-maintenance.md` for main README.md maintenance and content guidelines

**CRITICAL** The most commonly needed items are in the memory files above. Load only what you need for the current task.

## Quick Reference

```bash
# Essential commands
cargo build                    # Build workspace
cargo test                     # Run all tests
cargo build -p scope-core      # Build specific crate
cargo fmt && cargo clippy      # Format and lint
```

## Workspace Structure

```
scope/
├── scope-core/     # Core functionality
├── scope-cli/      # CLI interface
├── scope-web/      # Web interface
└── memory/         # Documentation system
```

Load specific memory files above for detailed information on each topic.