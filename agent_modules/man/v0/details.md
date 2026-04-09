# man — Agent Module Manual

## Purpose
Display human-readable documentation for any installed agent module.

## Usage
  man <parameter-name>

## How it works
1. Scans ~/defined-home-agents/ for files matching:
     activated_<name>_AGENTS.md
     deactivated_<name>_AGENTS.md
2. Reads the `details-location` field from the matched AGENT file.
3. Displays the content at that location.

## File pattern
  ~/defined-home-agents/{active_status}_{parameter-name}_AGENTS.md
  active_status: "activated_" | "deactivated_"

## Edge cases
- deactivated_: notify user of status before showing details
- multiple matches: display in order found
- no match: report "No agent module named '<name>' found."
