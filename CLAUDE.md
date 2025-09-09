# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is the **Binbash Leverage AI Prompt Library** - a comprehensive collection of prompt engineering templates, context engineering patterns, and multi-agent system designs for DevOps, Infrastructure-as-Code, and Cloud solutions. The library follows a structured approach to prompt engineering with comprehensive metadata for easy AI tool integration.

## Repository Structure

### Core Directories
- `prompts/` - Main prompt templates organized by domain:
  - `infrastructure/` - Terraform/OpenTofu modules, AWS services, validation
  - `architecture/` - Landing zone, data lake, GenAI stack patterns
  - `cli/` - Leverage CLI automation and scaffolding
  - `documentation/` - Technical writing, API docs, troubleshooting
  - `agents/` - Multi-agent orchestration and communication
- `schemas/` - JSON schemas for metadata validation
- `examples/` - Real-world implementation examples and workflows
- `tools/` - Validation, generation, and analysis utilities
- `docs/` - Comprehensive documentation and guides

### Important Files
- `.cursorrules` - Comprehensive Cursor IDE configuration with prompt standards
- `CONTRIBUTING.md` - Detailed contribution guidelines and standards
- `README.md` - Project overview and getting started guide

## Development Commands

### Validation Commands
```bash
# Validate entire library structure
python tools/validation/validate_library.py

# Validate specific prompt metadata
python tools/validation/validate_prompt.py prompts/path/to/prompt.md

# Check metadata schema compliance
python tools/validation/schema_check.py
```

### Generation Tools
```bash
# Create new prompt template
python tools/generation/create_prompt_template.py

# Update category indexes
python tools/generation/category_index.py

# Update cross-references between prompts
python tools/generation/cross_reference.py
```

### Analysis Tools
```bash
# Generate effectiveness reports
python tools/analysis/effectiveness_report.py

# Analyze usage statistics
python tools/analysis/usage_statistics.py

# Test model compatibility
python tools/analysis/model_compatibility.py
```

## Prompt Template Standards

All prompts must follow this exact metadata structure (from `.cursorrules`):

```yaml
---
name: "Descriptive Prompt Name"
description: "Clear description of what this prompt does"
category: "domain/subdomain"
use_cases: ["specific-use-case-1", "specific-use-case-2"]
model_compatibility: ["gpt-4o", "gpt-5", "claude-3.5-sonnet", "claude-4"]
effectiveness_rating: 8.5  # 1-10 scale
last_updated: "YYYY-MM-DD"
author: "Author Name"
tags: ["tag1", "tag2", "tag3"]
related_prompts: ["path/to/related-prompt.md"]
dependencies: ["external-tool-1", "external-tool-2"]
context_requirements:
  - "Required context item 1"
  - "Required context item 2"
performance_notes: "Notes about effectiveness, limitations, or improvements"
token_estimate:
  input_tokens: 300
  output_tokens: 1200
  context_tokens: 400
validation_status: "tested"  # draft, reviewed, tested, production
version: "1.0.0"
difficulty_level: "intermediate"
output_format: "markdown"
safety_considerations:
  - "Important safety consideration 1"
---
```

### Prompt Content Structure
1. **Role Definition** - Clear AI persona and expertise
2. **Context** - Background information and setup
3. **Task** - Specific, actionable instructions
4. **Output Format** - Expected response structure
5. **Examples** - Concrete input/output pairs
6. **Constraints** - Limitations and requirements
7. **Quality Criteria** - Success metrics

## File Naming Conventions

- Use kebab-case: `terraform-module-generator.md`
- Descriptive names indicating purpose
- Version suffix for multiple versions: `prompt-name-v2.md`

## Code Architecture Patterns

### Binbash Leverage Integration
- All infrastructure prompts align with Leverage Reference Architecture
- Use consistent Terraform/OpenTofu patterns with proper variable validation
- Follow environment-specific configurations (dev/staging/prod)
- Implement standard tagging strategies with `tags_common` variable
- Include security best practices (encryption, least-privilege IAM)

### Multi-Agent Coordination
- Design prompts for agent orchestration when applicable
- Specify clear boundaries and responsibilities
- Include inter-agent communication patterns
- Consider workflow dependencies and error handling

## Quality Standards

### Effectiveness Ratings (1-10 scale)
- **9-10**: Exceptional performance, consistently high-quality results
- **7-8**: Good performance with minor limitations
- **5-6**: Adequate but may need refinement
- **3-4**: Basic functionality with significant limitations
- **1-2**: Poor performance, needs major improvements

### Testing Requirements
- Test with at least 2 different AI models
- Validate with multiple use case scenarios
- Document specific strengths and limitations
- Include token usage estimates
- Verify metadata schema compliance

## Security Considerations

- Never include sensitive information in prompts
- Avoid hardcoded credentials or secrets
- Review for potential prompt injection vulnerabilities
- Consider data privacy in examples
- Validate security configurations in generated code

## Integration Notes

### Cursor IDE Integration
- Optimized `.cursorrules` file for AI assistance
- Structured prompts for easy AI parsing
- Context-rich metadata for better understanding
- Modular design for conversation inclusion

### Leverage CLI Compatibility
- Reference existing Leverage CLI commands
- Align with Leverage Reference Architecture
- Use Leverage terminology and conventions
- Support automation workflow patterns

## Git Workflow

### Branch Naming
- `feature/add-[prompt-name]` - New prompts
- `docs/improve-[area]` - Documentation updates  
- `fix/[issue-description]` - Bug fixes

### Commit Message Format (Conventional Commits)
```bash
feat(infrastructure): add terraform security scanner prompt
docs(guides): improve multi-agent pattern examples
fix(metadata): correct schema validation for tags field
```

## Pre-commit Checklist

- [ ] Metadata schema validation passes
- [ ] All required fields completed
- [ ] No sensitive information included
- [ ] Related prompts cross-referenced
- [ ] Effectiveness rating based on actual testing
- [ ] Safety considerations documented
- [ ] Dependencies clearly listed

## Performance Notes

The library maintains effectiveness ratings across different AI models and continuously updates prompts based on performance feedback. Token estimates help with cost optimization, and validation status tracks prompt maturity from draft to production-ready.