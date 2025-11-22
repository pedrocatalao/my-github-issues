# GitHub Issues Collector

A Python tool to collect and filter your assigned GitHub issues, including their status across multiple projects.

## Features

- **Collect Assigned Issues**: Fetches all issues assigned to you across all organizations.
- **Project Status**: Retrieves the status of the issue in GitHub Projects (V2).
- **Archived Status**: Indicates if the issue is archived in a project.
- **Filtering**: Filter results by Organization, Project, Status, and Archived state.
- **JSON Output**: Outputs clean, parsed JSON for easy integration with other tools.

## Setup

1. **Clone the repository** (or download the scripts).
2. **Run the helper script**:
   The `run.sh` script handles virtual environment creation and dependency installation automatically.

   ```bash
   chmod +x run.sh
   ```

3. **Export your GitHub Token**:
   You need a Personal Access Token (PAT) with `repo`, `read:org`, and `project` scopes.

   ```bash
   export GITHUB_TOKEN=ghp_your_token_here
   ```

## Usage

Run the tool using the `run.sh` script.

### Basic Usage
Collect all assigned issues:
```bash
./run.sh
```

### Filtering Examples

**Filter by Organization:**
```bash
./run.sh --org dovetailworld
```

**Filter by Project and Status:**
```bash
./run.sh --project DevOps --status "Sprint finished"
```

**Filter by Archived Status:**
```bash
# Show only non-archived items
./run.sh --is-archived false

# Show only archived items
./run.sh --is-archived true
```

**Combine Filters:**
```bash
./run.sh --org dovetailworld --project DevOps --status "In Progress" --is-archived false
```

## Output Format

```json
[
  {
    "issue_name": "Simplify deployment actions",
    "number": 301,
    "status": "CLOSED",
    "org": "dovetailworld",
    "repo": "devops",
    "projects": [
      {
        "project_name": "DevOps",
        "status": "Sprint finished",
        "is_archived": false
      }
    ]
  }
]
```
