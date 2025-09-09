# Contributing to Binbash Leverage AI Prompt Library

Thanks for helping improve AI-powered infrastructure automation! This guide will help you contribute effectively.

## 🎯 What We Need

**High Impact Contributions:**
- Prompts tested with real Leverage projects
- Integration examples with Leverage CLI
- AWS-specific infrastructure patterns
- Troubleshooting and operational guidance

## 🚀 Quick Start

1. **Fork** this repository
2. **Test** your prompts with actual Leverage projects  
3. **Document** effectiveness ratings based on real usage
4. **Submit** pull request with clear examples

## 📝 Prompt Standards

### Required Metadata
```yaml
---
name: "Descriptive Name"
description: "What this prompt does"
category: "leverage-cli|terraform-modules|reference-architecture|documentation"
use_cases: ["specific-use-case"]
model_compatibility: ["gpt-5", "gpt-4o", "claude-4-sonnet", "claude-3.5-sonnet"]
effectiveness_rating: 8.5  # Based on actual testing
last_updated: "YYYY-MM-DD"
author: "Your Name"
tags: ["relevant", "tags"]
version: "1.0.0"
---
```

### Categories
- **leverage-cli**: Project setup, environment management, automation
- **terraform-modules**: Module generation, validation, documentation
- **reference-architecture**: Landing zones, data lakes, GenAI stacks
- **documentation**: Technical writing, troubleshooting, guides

## 🧪 Testing Requirements

Before submitting:
- [ ] Test with at least 2 different AI models
- [ ] Use with real Leverage project scenarios
- [ ] Validate generated code/configurations
- [ ] Document what works well and limitations
- [ ] Include effectiveness rating (1-10) based on testing

## 📋 Pull Request Process

### Commit Format
```bash
git commit -m "feat(category): add [prompt name] for [use case]"
git commit -m "docs: improve setup examples in README"
git commit -m "fix(terraform): correct module validation logic"
```

### PR Template
```markdown
## Description
Brief description of the prompt and its purpose.

## Testing Results
- **Models tested**: GPT-5, Claude-4-Sonnet
- **Scenarios tested**: [describe test scenarios]
- **Effectiveness rating**: X.X/10
- **Key strengths**: [what works well]
- **Limitations**: [known issues or constraints]

## Integration
- [ ] Tested with Leverage CLI workflows
- [ ] Follows Leverage naming conventions
- [ ] References official Leverage resources
- [ ] Includes working code examples
```

## 🎯 Quality Standards

### Effectiveness Ratings
- **9-10**: Exceptional results, ready for production use
- **7-8**: Good performance with minor limitations
- **5-6**: Adequate but needs refinement
- **3-4**: Basic functionality, significant limitations
- **1-2**: Poor performance, major improvements needed

### Integration Requirements
- Reference [Leverage Documentation](https://leverage.binbash.co/)
- Use patterns from [le-tf-infra-aws](https://github.com/binbashar/le-tf-infra-aws)
- Follow [Leverage module conventions](https://github.com/binbashar/le-dev-tools/blob/master/terraform/Makefile)
- Align with AWS Well-Architected Framework

## 🔧 Development Tools

### Validation
```bash
# Validate prompt metadata
python -c "import json; json.load(open('schemas/prompt-metadata.json'))"

# Test prompt structure
grep -r "^---$" prompts/  # Check YAML frontmatter
```

## 🤝 Community

- **GitHub Issues**: Bug reports and feature requests
- **Discussions**: Questions and community input
- **Reviews**: Peer feedback on contributions

## 📈 Recognition

Contributors get:
- Attribution in prompt metadata
- Recognition in release notes
- Invitation to join maintainer team (for significant contributions)

---

**Start small, test thoroughly, document well.** Every contribution helps make AI-driven infrastructure more accessible! 🚀