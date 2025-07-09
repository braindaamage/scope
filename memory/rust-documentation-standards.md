# Rust Documentation Standards

## Overview

Rust documentation comments are the JSDoc equivalent for Rust code. Always add comprehensive documentation when creating software components.

## Documentation Comment Types

### Outer Doc Comments (`///`)
Used for documenting items (functions, structs, enums, etc.):

```rust
/// Calculates the sum of two numbers.
/// 
/// # Arguments
/// 
/// * `a` - The first number
/// * `b` - The second number
/// 
/// # Returns
/// 
/// The sum of `a` and `b`
/// 
/// # Examples
/// 
/// ```
/// let result = add(5, 3);
/// assert_eq!(result, 8);
/// ```
fn add(a: i32, b: i32) -> i32 {
    a + b
}
```

### Inner Doc Comments (`//!`)
Used for documenting modules or crates:

```rust
//! # My Module
//! 
//! This module provides utilities for mathematical operations.
//! 
//! ## Features
//! 
//! - Basic arithmetic operations
//! - Advanced mathematical functions
```

## Documentation Sections

### Standard Sections
- **Description**: Brief overview of functionality
- **Arguments**: Parameter descriptions using `* param_name - description`
- **Returns**: Description of return value
- **Examples**: Code examples with doctests
- **Panics**: When the function might panic
- **Errors**: Error conditions for Result types
- **Safety**: For unsafe functions

### Struct Documentation
```rust
/// Represents a user in the system.
/// 
/// # Fields
/// 
/// * `id` - Unique identifier
/// * `name` - User's display name
/// * `email` - User's email address
pub struct User {
    pub id: u64,
    pub name: String,
    pub email: String,
}
```

## Documentation Generation

### Commands
```bash
cargo doc                    # Generate documentation
cargo doc --open             # Generate and open in browser
cargo doc --no-deps          # Skip dependency docs
cargo test --doc             # Run doctests
```

### Doctests
Code blocks in documentation are automatically tested:
```rust
/// ```
/// let result = my_function(42);
/// assert_eq!(result, 84);
/// ```
```

## Best Practices

1. **Always document public APIs** - Every public function, struct, enum, and module
2. **Use examples** - Include practical usage examples
3. **Follow conventions** - Use standard section headers (Arguments, Returns, etc.)
4. **Keep updated** - Update docs when code changes
5. **Test examples** - Ensure doctest examples compile and pass
6. **Be concise** - Clear and brief explanations
7. **Link related items** - Use `[Type]` for cross-references

## Quick Reference

- `///` for item documentation
- `//!` for module documentation
- `#[doc = "text"]` for attribute-style docs
- `cargo doc` to generate HTML docs
- Code blocks become doctests by default