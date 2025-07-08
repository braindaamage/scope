# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Scope is a Rust-based "System for Contextual Orchestration of Projects & Execution" that provides intelligent project management, execution workflows, and context-aware automation. The project uses a Cargo workspace architecture with three main crates that work together to provide a complete solution.

## Architecture

This is a Cargo workspace with three main crates:

- **scope-core**: Core functionality and shared libraries - contains the fundamental orchestration engine, project management logic, and execution framework
- **scope-cli**: Command-line interface - provides CLI commands for interacting with the scope system
- **scope-web**: Web interface - provides a web-based interface for managing projects and execution workflows

All crates use workspace inheritance for common package metadata and share dependencies through the workspace configuration.

## Common Commands

### Build and Development
```bash
# Build the entire workspace
cargo build

# Build a specific crate
cargo build -p scope-core
cargo build -p scope-cli  
cargo build -p scope-web

# Run tests for the entire workspace
cargo test

# Run tests for a specific crate
cargo test -p scope-core

# Check code without building
cargo check

# Format code
cargo fmt

# Run clippy linter
cargo clippy
```

### Adding New Crates
```bash
# Create a new library crate in the workspace
cargo new --lib scope-newcrate

# Then add "scope-newcrate" to the members array in root Cargo.toml
```

## Workspace Configuration

The workspace defines common dependencies that are available to all crates:
- `tokio` - Async runtime with full features
- `serde` - Serialization framework with derive features
- `clap` - Command line argument parsing with derive features

When adding dependencies to individual crates, prefer using workspace dependencies where possible to maintain consistency.

## Development Workflow

1. This project targets Rust 1.70+ with 2021 edition
2. All crates inherit workspace package metadata (version, authors, license, etc.)
3. The project structure allows for independent development of each component while maintaining shared functionality through scope-core
4. The CLI and web interfaces should both depend on scope-core for shared functionality