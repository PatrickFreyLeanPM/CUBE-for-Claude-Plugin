---
name: cube-effort-estimation
description: Estimate development effort for backlog items in Story Points using Fibonacci-inspired scaling.
---

# cube-effort-estimation

Estimate development effort for backlog items in Story Points using Fibonacci-inspired scaling.

## Description
This skill estimates the development effort required for each backlog item in Story Points, which represents an abstract measure of both effort and complexity. It uses a Fibonacci-inspired sequence: 0, 1, 2, 3, 5, 8, 13, 20, 40, 70, etc.

## Usage
Apply this skill to a markdown backlog file to add a "Development Effort (Story Points)" column based on effort and complexity analysis.

## How it works
1. Reads a markdown file containing a backlog table
2. For each backlog item, estimates effort considering:
   - Implementation complexity
   - Technical uncertainty
   - Dependencies on other items
   - Required research or learning
   - Testing and validation needs
3. Assigns Story Points using the Fibonacci-inspired scale where:
   - 0-5: Simple, well-understood tasks
   - 8-13: Moderate complexity features
   - 20+: Complex epics or tasks with significant uncertainty
4. Outputs the enriched backlog with an additional effort column

## Example
Input backlog:
| ID | Title | Description |
|----|-------|-------------|
| 1 | User registration | Allow account creation with email/password |

Output:
| ID | Title | Description | Development Effort (Story Points) |
|----|-------|-------------|-----------------------------------|
| 1 | User registration | Allow account creation with email/password | 20 |

## Implementation
This skill applies effort estimation heuristics from the CUBE method:
- User registration/login: 13-20 SP (moderate complexity with security considerations)
- Biometric login: 20-40 SP (higher complexity due to platform-specific APIs)
- Social login: 8-13 SP (leveraging existing SDKs/APIs)
- Password reset: 5-8 SP (moderate complexity)
- Profile features: 5-13 SP (name: 5 SP, photo: 8 SP, video: 13 SP)
- Search positioning: 8 SP (algorithm implementation)
- Account deletion: 5 SP (straightforward but with data integrity considerations)
- Admin backend: 13-20 SP (CRUD interface for user management)
- Framework setup: 13 SP (project initialization and configuration)
- Environment setup: 20 SP (CI/CD pipeline configuration across multiple environments)

The actual estimation is performed by Claude's understanding of software development effort principles, calibrated to the Fibonacci-inspired Story Point scale described in the CUBE method documentation.