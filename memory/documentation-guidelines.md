# Project Documentation Guidelines

## Overview

All project documentation must follow file size guidelines, use Markdown format, and be organized in the `docs/` folder with clear structure.

## Core Requirements

### Location & Format
- **Location**: All docs in `docs/` folder
- **Format**: Markdown (.md) files only
- **Size Limits**: Follow file size guidelines (max 500 lines per file)
- **Organization**: Topic-based with clear hierarchy

### File Structure
```
docs/
├── README.md              # Main documentation index
├── getting-started/       # User onboarding
├── architecture/          # System design docs
├── api/                   # API documentation
├── development/           # Developer guides
└── examples/              # Code examples
```

## Organization Standards

### Main Index Pattern
- `docs/README.md` as central navigation
- Topic overview with links to detailed sections
- Keep index under 200 lines for clarity

### Topic Directories
- Group related documentation by theme
- Use descriptive directory names
- Include topic-specific README.md files

### File Naming
- Use kebab-case: `user-authentication.md`
- Be descriptive: `workspace-setup-guide.md`
- Avoid abbreviations: `configuration.md` not `config.md`

## Content Standards

### Structure Template
```markdown
# Topic Title

## Overview
Brief description...

## Key Concepts
- Concept 1
- Concept 2

## Implementation
Step-by-step guide...

## Examples
Practical examples...

## References
- [Related Topic](../other/topic.md)
- [External Link](https://example.com)
```

### File Size Management
- Split large docs by subtopic
- Use index files for navigation
- Cross-reference related content
- Maintain logical flow between files

### Quality Standards
- Clear, concise writing
- Practical examples included
- Regular review and updates
- Consistent formatting style

## Integration with Memory System

### Cross-References
- Link to relevant memory files
- Reference architecture decisions
- Connect to development workflows

### Maintenance
- Update docs with code changes
- Review during feature development
- Keep examples current and tested