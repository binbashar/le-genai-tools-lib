# Pull Request

## Description
Brief description of the changes and their purpose.

## Type of Change
Please delete options that are not relevant.

- [ ] 🐛 Bug fix (non-breaking change which fixes an issue)
- [ ] ✨ New prompt template
- [ ] 🔧 Enhancement to existing prompt
- [ ] 📚 Documentation update  
- [ ] 🛠️ Tool/utility improvement
- [ ] 🔨 Repository maintenance
- [ ] ⚠️ Breaking change (fix or feature that would cause existing functionality to not work as expected)

## Prompts Modified/Added
List the prompt files that were modified or added:

- `prompts/category/subcategory/prompt-name.md` - [Brief description of changes]

## Testing
Describe the testing you performed:

### AI Model Testing
- [ ] Tested with GPT-4
- [ ] Tested with Claude 3/3.5 Sonnet  
- [ ] Tested with other models (specify): ________________

### Test Cases
1. **Test Case 1**: [Description]
   - Input: [Example input]
   - Expected Output: [Expected result]
   - Actual Output: [Actual result]
   - Status: ✅ Pass / ❌ Fail

2. **Test Case 2**: [Description]
   - Input: [Example input]
   - Expected Output: [Expected result] 
   - Actual Output: [Actual result]
   - Status: ✅ Pass / ❌ Fail

### Validation
- [ ] Prompt validation passes: `python tools/validation/validate_prompt.py path/to/prompt.md`
- [ ] Library structure validation passes: `python tools/validation/validate_library.py`
- [ ] No broken cross-references

## Effectiveness Rating
For new or modified prompts, provide effectiveness rating based on testing:

- **Rating**: X.X/10
- **Based on**: [Number] test runs across [Number] scenarios
- **Key strengths**: [What works well]
- **Known limitations**: [Areas for improvement]

## Checklist
Please review and check all applicable items:

### Quality Standards
- [ ] Followed the prompt template format exactly
- [ ] All required metadata fields are complete and accurate
- [ ] Used appropriate category and subcategory
- [ ] Added relevant tags for discoverability
- [ ] Included proper use cases
- [ ] Set realistic effectiveness rating based on testing

### Content Quality
- [ ] Clear role definition and context
- [ ] Specific, actionable task description
- [ ] Appropriate output format specification
- [ ] Relevant examples included
- [ ] Proper constraints and quality criteria
- [ ] Integration notes where applicable

### Technical Requirements
- [ ] No sensitive information (API keys, passwords, etc.) included
- [ ] Related prompts are cross-referenced appropriately
- [ ] Dependencies are clearly documented
- [ ] Safety considerations addressed
- [ ] Token estimates provided (if applicable)

### Documentation
- [ ] Updated README.md if adding new category
- [ ] Updated CONTRIBUTING.md if changing standards
- [ ] Added/updated examples where helpful
- [ ] Spell-checked and grammar-checked

### Validation
- [ ] Metadata schema validation passes
- [ ] File naming follows kebab-case convention
- [ ] File is in correct directory structure
- [ ] Links and references are valid

## Impact Assessment
Describe the impact of your changes:

### Positive Impact
- [Impact 1]: Description
- [Impact 2]: Description

### Potential Risks
- [Risk 1]: Description and mitigation strategy
- [Risk 2]: Description and mitigation strategy

### Backward Compatibility
- [ ] These changes are fully backward compatible
- [ ] These changes may affect existing users (explain below)
- [ ] These changes are breaking changes (explain below)

**Compatibility Details**: [If applicable, explain impact on existing users]

## Related Issues
Link related issues and discussions:

- Closes #[issue number]
- Related to #[issue number]
- Addresses feedback from #[issue number]

## Additional Context
Add any other context, screenshots, or examples that help explain your changes:

## Reviewer Notes
Anything specific you'd like reviewers to focus on:

---

**For Maintainers**

### Review Checklist
- [ ] Code quality meets standards
- [ ] Documentation is complete and accurate  
- [ ] Testing is adequate
- [ ] No security concerns
- [ ] Follows project conventions
- [ ] Ready for merge

### Post-Merge Actions
- [ ] Update effectiveness tracking
- [ ] Monitor for user feedback
- [ ] Consider for next release notes