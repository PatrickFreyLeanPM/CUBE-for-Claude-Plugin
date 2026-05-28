---
name: cube-release-planning
description: Organize prioritized backlog items into incremental releases (V0, V1, V2, etc.) based on effort capacity.
---

# cube-release-planning

Organize prioritized backlog items into incremental releases (V0, V1, V2, etc.) based on effort capacity.

## Description
This skill groups backlog items into product versions/releases based on their priority (ROI) and the development team's capacity per release. It follows the CUBE method's release planning approach:
- V0: Infrastructure setup (Operational Efficiency items)
- V1..Vn: MVP versions focusing on Basic customer value and New Business
- Vn+1..Vm: Expanded versions for Retainment and Performance/Delighter items
- Vm+1: Maintenance and expansion focusing on Operational Efficiency and Up Sell

## Usage
Apply this skill to a markdown backlog file that has been prioritized by ROI (contains ROI Ratio column) to add a "Version" column assigning items to releases.

## How it works
1. Reads a markdown file containing a prioritized backlog table with ROI Ratio column
2. Applies CUBE release planning heuristics:
   - V0: Assigns items with Business Value Category = "Operational Efficiency" that are required for setup
   - V1: Assigns high-ROI items with Customer Value = "Basic" and Business Value Category = "New Business" until capacity is reached
   - Subsequent versions: Continue assigning items by ROI priority, considering customer and business value focus for each version type
   - Respects effort capacity per version (typically 35-40 Story Points as per CUBE method example)
3. Outputs the backlog with an additional "Version" column indicating target release for each item

## Example
Input backlog (prioritized by ROI):
| ID | Title | Description | ROI Ratio | Version |
|----|-------|-------------|-----------|---------|
| 7 | User profile: Name | Let users set display name | 400 |  |

Output:
| ID | Title | Description | ROI Ratio | Version |
|----|-------|-------------|-----------|---------|
| 7 | User profile: Name | Let users set display name | 400 | V1 |

## Implementation
This skill implements the CUBE method's release planning logic:
- Analyzes each item's Customer Value, Business Value Category, and ROI
- Assigns to V0: Infrastructure/enabling items (Operational Efficiency)
- Assigns to V1: Basic customer value items that enable New Business
- Distributes remaining items across versions by ROI priority, considering:
  * V2: Balance of Basic, Performance, Delighter for early adopters
  * V3-Vn: Performance/Delighter for Retention and Up Sell
  * Vn+1: Operational Efficiency improvements and Up Sell features
- Tracks cumulative Story Points per version to stay within team capacity
- The actual assignment follows the principles and examples from the CUBE method documentation