# File Size Guidelines & Best Practices

## Overview

Maintain optimal file sizes for better maintainability, readability, and development efficiency.

## File Size Limits

### Code Files (Rust)
- **Maximum**: 300 lines
- **Strategy**: Decompose into modules, traits, or separate components
- **Focus**: Single responsibility principle per file

### Documentation Files
- **Maximum**: 500 lines  
- **Strategy**: Separate by topic with index references
- **Pattern**: Main file with links to topic-specific files

### Memory Files
- **Maximum**: 100 lines
- **Strategy**: Use index reference pattern
- **Pattern**: Concise summary with cross-references

## Decomposition Strategies

### Large Code Files
```rust
// Instead of one large file:
// src/large_module.rs (400+ lines)

// Split into:
// src/module/mod.rs       - Public interface
// src/module/core.rs      - Core functionality  
// src/module/types.rs     - Type definitions
// src/module/utils.rs     - Utility functions
```

### Large Documentation
```markdown
# Main file: feature.md
## Overview
Brief description...

## Detailed Topics
- [Implementation](feature/implementation.md)
- [Configuration](feature/configuration.md)
- [Examples](feature/examples.md)
```

### Memory File Pattern
```markdown
# Topic Overview
Brief summary...

## Key Points
- Point 1
- Point 2

## References
- [Details](topic/details.md)
- [Examples](topic/examples.md)
```

## Implementation Guidelines

### When to Split
- Code file approaches 250 lines
- Documentation exceeds 400 lines
- Memory file reaches 80 lines

### File Organization
- Group related functionality
- Use clear, descriptive names
- Maintain logical file structure
- Create index files for navigation

## Quality Checklist
- [ ] Files stay within size limits
- [ ] Clear separation of concerns
- [ ] Proper cross-referencing
- [ ] Logical file organization