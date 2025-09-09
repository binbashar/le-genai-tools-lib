# Complete Leverage Project Setup Example

This example demonstrates using the Leverage AI Prompt Library to set up a complete infrastructure project from scratch.

## Scenario
Setting up infrastructure for a web application with development and production environments.

## Step 1: Project Initialization

**Prompt Used**: `prompts/leverage-cli/project-setup-assistant.md`

**AI Input**: 
"I need to set up a new Leverage project for a web application called 'TaskFlow' with development and production environments. We're a team of 5 developers and need basic AWS services like EC2, RDS, and S3."

**AI Output**:
Generated complete `project.yaml` configuration and step-by-step setup commands.

## Step 2: Terraform Module Creation

**Prompt Used**: `prompts/terraform-modules/leverage-module-generator.md`

**AI Input**:
"Create a Terraform module for an Application Load Balancer with auto-scaling group integration for our TaskFlow application."

**AI Output**:
Complete Terraform module with all required files, security configurations, and usage examples.

## Step 3: Architecture Guidance

**Prompt Used**: `prompts/reference-architecture/landing-zone-advisor.md`

**AI Input**:
"Design a secure multi-account setup for TaskFlow with proper governance and security baselines."

**AI Output**:
Detailed architecture recommendations with Control Tower setup and security baseline configurations.

## Step 4: Documentation Creation

**Prompt Used**: `prompts/documentation/leverage-docs-assistant.md`

**AI Input**:
"Create deployment documentation for the TaskFlow infrastructure including troubleshooting steps."

**AI Output**:
Comprehensive documentation with step-by-step deployment guide and common issue resolutions.

## Results

- **Time Saved**: ~40 hours of initial setup and configuration
- **Quality**: Production-ready configurations following Leverage best practices
- **Consistency**: All components follow established patterns and conventions
- **Documentation**: Complete operational procedures and troubleshooting guides

## Key Success Factors

1. **Clear Requirements**: Specific, detailed input to the AI prompts
2. **Iterative Refinement**: Using AI output as starting point, then customizing
3. **Testing**: Validating all generated configurations in development environment
4. **Integration**: Ensuring all components work together in Leverage ecosystem

## Files Generated

```
taskflow-infrastructure/
├── project.yaml                    # Leverage project configuration
├── shared/
│   ├── base-tf-backend/           # Terraform state management
│   ├── base-identities/           # IAM roles and policies
│   └── base-network/              # VPC and networking
├── dev/
│   ├── applications/              # Application infrastructure
│   └── data/                      # Database configurations
├── prod/
│   ├── applications/              # Production application setup
│   └── data/                      # Production database setup
├── modules/
│   └── alb-asg/                   # Custom ALB + ASG module
└── docs/
    ├── deployment-guide.md        # Deployment procedures
    └── troubleshooting.md         # Common issues and solutions
```

## Lessons Learned

- **Start Simple**: Begin with basic configurations and add complexity iteratively
- **Validate Early**: Test each component before moving to the next
- **Document Everything**: Use the documentation prompts to maintain good records
- **Follow Patterns**: Stick to Leverage conventions for consistency and maintainability
