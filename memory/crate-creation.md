# Crate Creation Guide

## Adding New Crates to the Workspace

### Step-by-Step Process

1. **Create the new crate directory and structure**
   ```bash
   # Create new library crate
   cargo new --lib scope-newcrate
   
   # Or create binary crate
   cargo new --bin scope-newcrate
   ```

2. **Configure the crate's Cargo.toml**
   ```toml
   [package]
   name = "scope-newcrate"
   version.workspace = true
   edition.workspace = true
   authors.workspace = true
   description = "Description of your new crate"
   license.workspace = true
   repository.workspace = true
   keywords.workspace = true
   categories.workspace = true
   
   [dependencies]
   # Add dependencies here
   ```

3. **Update workspace members**
   Add the new crate to the workspace members in root `Cargo.toml`:
   ```toml
   [workspace]
   members = [
       "scope-core",
       "scope-cli",
       "scope-web",
       "scope-newcrate"  # Add your new crate here
   ]
   ```

4. **Verify the setup**
   ```bash
   # Check that workspace recognizes the new crate
   cargo check -p scope-newcrate
   
   # Build the new crate
   cargo build -p scope-newcrate
   ```

## Naming Conventions

### Crate Names
- Use `scope-` prefix for all crates
- Use kebab-case for crate names
- Be descriptive: `scope-config`, `scope-metrics`, `scope-storage`

### Common Crate Types
- **scope-core**: Core functionality (already exists)
- **scope-cli**: Command line interface (already exists)  
- **scope-web**: Web interface (already exists)
- **scope-config**: Configuration management
- **scope-storage**: Data persistence
- **scope-metrics**: Metrics and monitoring
- **scope-plugins**: Plugin system

## Crate Types and Structure

### Library Crates (`--lib`)
```
scope-newcrate/
├── Cargo.toml
├── src/
│   ├── lib.rs          # Main library entry point
│   ├── types.rs        # Type definitions
│   └── utils.rs        # Utility functions
└── tests/
    └── integration.rs  # Integration tests
```

### Binary Crates (`--bin`)
```
scope-newcrate/
├── Cargo.toml
├── src/
│   ├── main.rs         # Binary entry point
│   ├── lib.rs          # Library code
│   └── cli.rs          # CLI-specific code
└── tests/
    └── integration.rs  # Integration tests
```

## Dependencies Between Crates

### Dependency Guidelines
- **scope-core**: Should not depend on CLI or web crates
- **scope-cli**: Should depend on scope-core
- **scope-web**: Should depend on scope-core
- **New crates**: Consider if they should depend on core or be standalone

### Adding Inter-Crate Dependencies
```toml
# In scope-newcrate/Cargo.toml
[dependencies]
scope-core = { path = "../scope-core" }
```

## Best Practices

### When to Create a New Crate
- Feature is large enough to warrant separation
- Code can be reused across CLI and web interfaces
- Functionality is logically distinct
- Testing isolation is beneficial

### Crate Design Principles
- **Single Responsibility**: Each crate should have a clear purpose
- **Minimal API**: Expose only what's necessary
- **Documentation**: Document public APIs thoroughly
- **Testing**: Include comprehensive tests

### File Organization
```
scope-newcrate/src/
├── lib.rs              # Public API and re-exports
├── error.rs            # Error types
├── config.rs           # Configuration structures
├── core/               # Core functionality
│   ├── mod.rs
│   └── implementation.rs
└── utils/              # Utility modules
    ├── mod.rs
    └── helpers.rs
```

## Common Patterns

### Error Handling
```rust
// In src/error.rs
#[derive(Debug, thiserror::Error)]
pub enum NewCrateError {
    #[error("Configuration error: {0}")]
    Config(String),
    #[error("IO error: {0}")]
    Io(#[from] std::io::Error),
}

pub type Result<T> = std::result::Result<T, NewCrateError>;
```

### Public API Design
```rust
// In src/lib.rs
pub mod config;
pub mod core;
pub mod error;

pub use error::{NewCrateError, Result};
pub use core::NewCrateService;

// Re-export commonly used types
pub use config::NewCrateConfig;
```

## Testing New Crates

### Unit Tests
```rust
// In src/lib.rs or separate files
#[cfg(test)]
mod tests {
    use super::*;
    
    #[test]
    fn test_functionality() {
        // Test implementation
    }
}
```

### Integration Tests
```rust
// In tests/integration.rs
use scope_newcrate::*;

#[test]
fn test_integration() {
    // Integration test implementation
}
```

### Running Tests
```bash
# Test specific crate
cargo test -p scope-newcrate

# Test all crates
cargo test
```