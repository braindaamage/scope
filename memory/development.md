# Development Workflow & Best Practices

## Development Environment

### Requirements
- Rust 1.70+ (2021 edition)
- Cargo (comes with Rust)
- Git for version control

### Recommended Tools
- `cargo-watch` for automatic rebuilding: `cargo install cargo-watch`
- `cargo-edit` for dependency management: `cargo install cargo-edit`
- IDE with Rust support (VS Code with rust-analyzer, IntelliJ IDEA, etc.)

## Development Workflow

### 1. Setting Up Development
```bash
# Clone and build
git clone <repository>
cd scope
cargo build

# Run tests to verify setup
cargo test
```

### 2. Working with Crates
- All crates inherit workspace package metadata
- Use workspace dependencies when possible
- Independent development of CLI and web interfaces
- Both depend on scope-core for shared functionality

### 3. Code Organization
```
scope/
├── scope-core/src/     # Core functionality
├── scope-cli/src/      # CLI implementation  
├── scope-web/src/      # Web interface
└── memory/             # Documentation system
```

### 4. Development Practices

#### Code Quality
- Run `cargo fmt` before committing
- Use `cargo clippy` to catch common mistakes
- Write tests for new functionality
- Document public APIs with doc comments

#### Testing Strategy
- Unit tests in each crate
- Integration tests in `tests/` directories
- Test CLI commands and web endpoints
- Mock external dependencies

#### Git Workflow
- Use feature branches for new development
- Write descriptive commit messages
- Run tests before pushing
- Create pull requests for code review

## Best Practices

### Dependency Management
- Prefer workspace dependencies for consistency
- Add new dependencies thoughtfully
- Keep dependencies up to date with `cargo update`
- Use specific versions for stability

### Error Handling
- Use `Result<T, E>` for error-prone operations
- Create custom error types for domain-specific errors
- Provide helpful error messages
- Use `?` operator for error propagation

### Documentation
- Document all public functions and types
- Include examples in doc comments
- Update CLAUDE.md and memory files when adding features
- Write clear README files for significant changes

### Performance
- Use `cargo build --release` for production builds
- Profile code with `cargo bench` when needed
- Consider async/await for I/O operations
- Use appropriate data structures for performance

## Common Development Tasks

### Adding New Functionality
1. Determine which crate should contain the feature
2. Add to scope-core if it's shared functionality
3. Write tests before implementation
4. Update documentation

### Debugging
- Use `cargo check` for quick syntax checking
- Add `println!` or `dbg!` macros for debugging
- Use `cargo test -- --nocapture` to see test output
- Enable logging with appropriate log levels

### Releasing
- Update version in workspace Cargo.toml
- Run full test suite
- Update changelog
- Create git tag for release