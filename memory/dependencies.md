# Workspace Dependencies & Management

## Workspace Dependencies

The workspace defines common dependencies that are available to all crates for consistency and version management.

### Current Workspace Dependencies

```toml
[workspace.dependencies]
tokio = { version = "1.0", features = ["full"] }
serde = { version = "1.0", features = ["derive"] }
clap = { version = "4.0", features = ["derive"] }
```

### Dependency Purposes

- **tokio**: Async runtime with full features for async/await operations
- **serde**: Serialization framework with derive macros for JSON, YAML, etc.
- **clap**: Command line argument parsing with derive macros for CLI

## Dependency Management Best Practices

### Using Workspace Dependencies

When adding dependencies to individual crates, prefer workspace dependencies:

```toml
# In individual crate Cargo.toml
[dependencies]
tokio = { workspace = true }
serde = { workspace = true, features = ["json"] }  # Can add extra features
```

### Adding New Workspace Dependencies

```bash
# Add to workspace from root directory
cargo add tokio --workspace --features full

# Add to specific crate
cargo add reqwest --package scope-web
```

### Common Dependencies by Crate

#### scope-core
- `tokio` - Async runtime for orchestration
- `serde` - Serialization for configuration and data
- Additional: `uuid`, `chrono`, `thiserror`

#### scope-cli  
- `clap` - Command line parsing
- `tokio` - Async operations
- `serde` - Configuration loading
- Additional: `colored`, `indicatif`

#### scope-web
- `tokio` - Async web server
- `serde` - JSON serialization
- Additional: `axum`, `tower`, `hyper`

## Version Management

### Workspace Version Strategy
- All crates inherit version from workspace
- Single source of truth for version numbers
- Synchronized releases across all crates

### Dependency Updates
```bash
# Update all dependencies
cargo update

# Update specific dependency
cargo update tokio

# Check for outdated dependencies (requires cargo-outdated)
cargo outdated
```

## Development Dependencies

### Testing Dependencies
```toml
[dev-dependencies]
tokio-test = "0.4"
serde_json = "1.0"
tempfile = "3.0"
```

### Build Dependencies
```toml
[build-dependencies]
# For build scripts if needed
```

## Feature Flags

### Workspace Feature Management
- Use feature flags for optional functionality
- CLI and web can enable different feature sets
- Core crate provides feature flags for optional components

### Example Feature Usage
```toml
[features]
default = ["cli", "web"]
cli = ["clap"]
web = ["axum", "tower"]
full = ["cli", "web", "metrics"]
```

## License and Metadata

### Workspace Metadata Inheritance
```toml
[workspace.package]
name = "scope"
version = "0.1.0"
edition = "2021"
authors = ["Your Name <your.email@example.com>"]
license = "MIT OR Apache-2.0"
repository = "https://github.com/yourusername/scope"
keywords = ["orchestration", "project", "execution", "system"]
categories = ["development-tools"]
```

All crates automatically inherit these fields unless explicitly overridden.