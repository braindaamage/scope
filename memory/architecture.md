# Workspace Architecture

## Overview

Scope uses a Cargo workspace architecture with three main crates that work together to provide a complete contextual orchestration system for projects and execution workflows.

## Core Architecture

### Three-Crate Structure

1. **scope-core** - Core functionality and shared libraries
   - Contains the fundamental orchestration engine
   - Project management logic and data structures  
   - Execution framework and workflow coordination
   - Shared utilities and common types
   - Business logic that both CLI and web interfaces depend on

2. **scope-cli** - Command-line interface
   - CLI commands for interacting with the scope system
   - Command-line argument parsing and validation
   - Terminal-based user interaction
   - Depends on scope-core for functionality

3. **scope-web** - Web interface  
   - Web-based interface for managing projects
   - HTTP API endpoints and web server
   - Frontend interface for execution workflows
   - Depends on scope-core for functionality

## Dependency Flow

```
scope-cli ──┐
            ├─→ scope-core (shared functionality)
scope-web ──┘
```

Both CLI and web interfaces depend on scope-core, but they do not depend on each other. This allows for independent development and deployment.

## Workspace Configuration

### Package Inheritance
All crates inherit common metadata from the workspace:
- Version, authors, license information
- Repository, keywords, categories
- Common build settings and edition (2021)

### Dependency Management
- Shared dependencies defined in workspace root
- Individual crates can add specific dependencies
- Workspace dependencies ensure version consistency

## Design Principles

1. **Separation of Concerns**: Each crate has a specific responsibility
2. **Shared Core**: Common functionality centralized in scope-core
3. **Interface Independence**: CLI and web can be developed separately
4. **Workspace Benefits**: Unified building, testing, and dependency management

## Module Structure (Planned)

### scope-core modules:
- `orchestration/` - Core orchestration engine
- `project/` - Project management functionality
- `execution/` - Execution framework
- `config/` - Configuration management
- `utils/` - Shared utilities

### scope-cli modules:
- `commands/` - CLI command implementations
- `cli/` - CLI parsing and interface
- `main.rs` - CLI entry point

### scope-web modules:
- `api/` - HTTP API endpoints
- `server/` - Web server implementation
- `handlers/` - Request handlers