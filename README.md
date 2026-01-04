# User Service Architecture Design

Design document for a high-scale, Cognito-authenticated User service on AWS Serverless Framework.

**Time-boxed to a single day of implementation** - demonstrating pragmatic trade-offs between completeness and delivery.

## Live Documentation

**[https://docs.esakrissa.com](https://docs.esakrissa.com)**

## Highlights

This design document demonstrates:

- **Pragmatic scoping** - Day 1 deliverables vs. future iterations clearly defined
- **Design decisions with rationale** - Why Serverless Framework over SAM/CDK, why EventBridge over SNS+SQS
- **Edge case handling** - Email uniqueness, primary email invariant, concurrent updates
- **Failure mode analysis** - What breaks, how we detect it, how we recover
- **Cost awareness** - Estimates at 10K, 100K, and 1M MAU scales
- **Security best practices** - OIDC for CI/CD, no long-lived credentials

## Document Structure

| Section | Key Topics |
|---------|------------|
| Introduction | Overview, design principles, **Day 1 scope** |
| Architecture | System components, request flow, **design decisions** |
| Data Model | DynamoDB single-table, GSI design, access patterns |
| Authentication | Cognito integration, **trigger failure recovery**, token revocation |
| API Design | Endpoints, edge cases, **rate limiting implementation** |
| Inter-Service | EventBridge events, ordering, guaranteed delivery |
| DevOps | IaC, CI/CD with **OIDC**, **cost analysis**, **testing strategy** |
| Hard Parts | Challenges, solutions, **failure mode analysis** |

## Tech Stack

| Component | Technology |
|-----------|------------|
| Runtime | Node.js 20.x LTS with TypeScript |
| Framework | Serverless Framework |
| Database | DynamoDB (single-table design) |
| Auth | AWS Cognito |
| Events | Amazon EventBridge |
| IaC | Terraform (shared resources) + Serverless (Lambda lifecycle) |
| CI/CD | GitHub Actions with OIDC federation |

## Quick Links

- [Day 1 Scope](https://docs.esakrissa.com/introduction#day-1-scope)
- [Design Decisions](https://docs.esakrissa.com/architecture#design-decisions)
- [Failure Mode Analysis](https://docs.esakrissa.com/hard-parts#failure-mode-analysis)
- [Cost Analysis](https://docs.esakrissa.com/devops#cost-analysis)

## Author

**Esa Krissa**
- GitHub: [github.com/esakrissa](https://github.com/esakrissa)
- Website: [esakrissa.com](https://esakrissa.com)
