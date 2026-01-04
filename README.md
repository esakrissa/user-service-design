# User Service Architecture Design

Design document for a high-scale, Cognito-authenticated User service on AWS Serverless Framework.

## Live Documentation

**[https://docs.esakrissa.dev](https://docs.esakrissa.dev)**

## Overview

This document covers the architecture design for a User Service that handles CRUD operations on User and Email entities. Key aspects include:

- **DynamoDB single-table design** with GSI for email lookups
- **AWS Cognito authentication** with JWT token flow
- **EventBridge** for inter-service communication
- **Edge case handling** for email uniqueness, primary email invariant, and concurrency
- **DevOps considerations** including Terraform, Serverless Framework, CI/CD, and monitoring

## Document Structure

| Section | Description |
|---------|-------------|
| Introduction | Overview and design principles |
| Architecture | System components and request flow |
| Data Model | DynamoDB schema and access patterns |
| Authentication | Cognito integration and token handling |
| API Design | Endpoints and edge cases |
| Inter-Service | EventBridge events and consumers |
| DevOps | IaC, CI/CD, monitoring, scaling |
| Hard Parts | Technical challenges and solutions |

## Tech Stack

- **Runtime:** Node.js 20.x with TypeScript
- **Framework:** Serverless Framework
- **Database:** DynamoDB (single-table design)
- **Auth:** AWS Cognito
- **Events:** Amazon EventBridge
- **IaC:** Terraform + Serverless Framework
- **CI/CD:** GitHub Actions

## Author

**Esa Krissa**
- GitHub: [github.com/esakrissa](https://github.com/esakrissa)
- Website: [esakrissa.com](https://esakrissa.com)
