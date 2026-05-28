---
name: cube-roi-calculation
description: Calculate Return on Investment (ROI) for backlog items and sort by priority.
---

# cube-roi-calculation

Calculate Return on Investment (ROI) for backlog items and sort by priority.

## Description
This skill calculates the Return on Investment (ROI) for each backlog item by dividing Business Value by Development Effort (Story Points). It then sorts the backlog items by ROI in descending order to prioritize items that deliver the highest business value per unit of effort.

## Usage
Apply this skill to a markdown backlog file that already contains Business Value and Development Effort columns to add an "ROI Ratio" column and sort items by priority.

## How it works
1. Reads a markdown file containing a backlog table with Business Value and Development Effort columns
2. For each backlog item, calculates ROI = Business Value ÷ Development Effort
3. Sorts all items by ROI ratio in descending order (highest ROI first)
4. Outputs the enriched backlog with an additional "ROI Ratio" column, sorted by priority

## Example
Input backlog:
| ID | Title | Description | Business Value | Development Effort |
|----|-------|-------------|----------------|-------------------|
| 1 | User registration | Allow account creation | 3000 | 20 |

Output:
| ID | Title | Description | Business Value | Development Effort | ROI Ratio |
|----|-------|-------------|----------------|-------------------|-----------|
| 1 | User registration | Allow account creation | 3000 | 20 | 150 |

## Implementation
This skill follows the CUBE method's ROI calculation:
- ROI = Business Value / Development Effort
- Higher ROI indicates better return on development investment
- Items are sorted by ROI to create a priority order
- The skill handles both integer and decimal ROI values
- Maintains all existing columns while adding the ROI calculation

The sorted output allows teams to easily identify which backlog items provide the most value for the least effort, supporting the CUBE method's goal of maximizing return-on-investment in development activities.