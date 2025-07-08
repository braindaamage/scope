# Commands & Development Workflows

## Build Commands

### Basic Build Operations
```bash
# Build the entire workspace
cargo build

# Build a specific crate
cargo build -p scope-core
cargo build -p scope-cli  
cargo build -p scope-web

# Build with optimizations (release mode)
cargo build --release
cargo build --release -p scope-core
```

### Testing Commands
```bash
# Run tests for the entire workspace
cargo test

# Run tests for a specific crate
cargo test -p scope-core
cargo test -p scope-cli
cargo test -p scope-web

# Run tests with output
cargo test -- --nocapture

# Run specific test
cargo test test_name
cargo test -p scope-core test_name
```

### Code Quality Commands
```bash
# Check code without building (faster)
cargo check

# Check specific crate
cargo check -p scope-core

# Format code
cargo fmt

# Check formatting without changing files
cargo fmt --check

# Run clippy linter
cargo clippy

# Run clippy with all targets
cargo clippy --all-targets

# Run clippy with pedantic lints
cargo clippy -- -W clippy::pedantic
```

### Documentation Commands
```bash
# Generate and open documentation
cargo doc --open

# Generate documentation for specific crate
cargo doc -p scope-core --open

# Generate documentation with private items
cargo doc --document-private-items
```

### Dependency Management
```bash
# Update dependencies
cargo update

# Add dependency to workspace
cargo add tokio --workspace

# Add dependency to specific crate
cargo add serde --package scope-core

# Remove dependency
cargo remove tokio --package scope-core
```

### Development Workflow Commands
```bash
# Watch and rebuild on changes (requires cargo-watch)
cargo watch -x check
cargo watch -x test
cargo watch -x "build -p scope-core"

# Clean build artifacts
cargo clean

# Tree view of dependencies
cargo tree
cargo tree -p scope-core
```