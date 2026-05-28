---
name: cube-business-analysis
description: Analyze backlog items from the business perspective to categorize business value and assign numerical scores.
---

# cube-business-analysis

Analyze backlog items from the business perspective to categorize business value and assign numerical scores.

## Description
This skill categorizes backlog items according to business value types (New Business, Up Sell, Retainment, Operational Efficiency) and assigns numerical business value scores using a Fibonacci-inspired sequence (100, 200, 300, 500, 800, 1300, 2000, 3000).

## Usage
Apply this skill to a markdown backlog file to add "Business Value Category" and "Business Value" columns based on business impact analysis.

## How it works
1. Reads a markdown file containing a backlog table
2. For each backlog item, determines the business value category:
   - New Business: Features that bring new customers or markets
   - Up Sell: Features that generate additional revenue from existing customers
   - Retainment: Features that prevent losing existing customers
   - Operational Efficiency: Features that save money or reduce costs
3. Assigns a numerical business value score based on relative importance within each category
4. Outputs the enriched backlog with additional columns

## Example
Input backlog:
| ID | Title | Description |
|----|-------|-------------|
| 1 | User registration | Allow account creation with email/password |

Output:
| ID | Title | Description | Business Value Category | Business Value |
|----|-------|-------------|-------------------------|----------------|
| 1 | User registration | Allow account creation with email/password | 1 - New Business | 3000 |

## Implementation
This skill applies business value heuristics from the CUBE method:
- User registration/login: Typically New Business (high value for acquiring customers)
- Social login: New Business (acquisition channel)
- Profile features: Often Retainment (keep existing users engaged)
- Password reset/Delete account: Operational Efficiency (reduce support costs)
- Admin backend: Operational Efficiency (internal tool)
- Setup/infrastructure: Operational Efficiency (enables development)
- Search positioning feature: Up Sell (potential premium feature)

Numerical scores are assigned relatively within categories based on perceived business impact, following the Fibonacci-inspired sequence multiplied by 100 as described in the CUBE method documentation.