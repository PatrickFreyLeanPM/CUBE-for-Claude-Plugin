---
name: cube-customer-analysis
description: Analyze backlog items from the customer perspective using the Kano model to classify customer value.
---

# cube-customer-analysis

Analyze backlog items from the customer perspective using the Kano model to classify customer value.

## Description
This skill applies the Kano model to classify backlog items according to customer value categories: Basic, Performance, Delighter, Unimportant, or Rejection. It helps understand how customers would perceive and value each feature.

## Usage
Apply this skill to a markdown backlog file to add a "Customer Value" column based on Kano model classification.

## How it works
1. Reads a markdown file containing a backlog table with at least ID, Title, and Description columns
2. For each backlog item, applies Kano model classification logic:
   - Basic: Features customers expect and take for granted; cause dissatisfaction if missing
   - Performance: Features where more is better; directly satisfy customers when present
   - Delighter: Unexpected features that delight customers when present but don't cause dissatisfaction if missing
   - Unimportant: Features customers don't care about either way
   - Rejection: Features that cause dissatisfaction when present
3. Outputs the enriched backlog with an additional "Customer Value" column

## Example
Input backlog:
| ID | Title | Description |
|----|-------|-------------|
| 1 | User registration | Allow account creation with email/password |

Output:
| ID | Title | Description | Customer Value |
|----|-------|-------------|----------------|
| 1 | User registration | Allow account creation with email/password | Basic |

## Implementation
This skill works by analyzing the semantic meaning of backlog items and applying Kano model heuristics:
- Login/account features typically classified as Basic
- Biometric login (fingerprint/FaceID) as Performance/Delighter
- Social login as Performance/Delighter
- Password reset as Basic/Rejection Point
- Profile features ranging from Basic (name) to Delighter (video)
- Admin/backend features often Unimportant
- Setup/infrastructure tasks typically Unimportant

The actual classification is performed by Claude's understanding of the Kano model principles described in the CUBE method documentation.