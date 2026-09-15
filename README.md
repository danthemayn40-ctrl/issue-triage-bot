# Issue Triage Bot

A GitHub Action that automatically triages new issues and pull requests. It labels, summarizes, and helps maintainers quickly understand and categorize incoming issues.

## Features

- **Auto-labeling**: Categorizes issues based on keywords and content
- **Summarization**: Generates concise summaries for long issue descriptions
- **Duplicate detection**: Identifies potential duplicate issues
- **Priority detection**: Suggests priority levels based on keywords
- **Component detection**: Identifies which parts of the codebase are affected

## Usage

Add this to your workflow file (e.g., `.github/workflows/issue-triage.yml`):

```yaml
name: Issue Triage
on:
  issues:
    types: [opened, reopened]
  pull_request:
    types: [opened, reopened]

jobs:
  triage:
    runs-on: ubuntu-latest
    permissions:
      issues: write
      pull-requests: write
    steps:
      - name: Triage Issue
        uses: your-username/issue-triage-bot@v1
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
          config-path: '.github/issue-triage.yml'
```

## Configuration

Create `.github/issue-triage.yml` in your repository:

```yaml
labels:
  bug:
    keywords: ['bug', 'error', 'crash', 'broken']
    color: 'd73a4a'
  feature:
    keywords: ['feature', 'enhancement', 'request']
    color: 'a2eeef'
  documentation:
    keywords: ['docs', 'readme', 'documentation']
    color: '0075ca'
  question:
    keywords: ['question', 'help', 'how to']
    color: 'd876e3'

priority:
  keywords:
    high: ['urgent', 'critical', 'blocker', 'security']
    medium: ['important']
    low: []
```

## License

MIT License - see [LICENSE](LICENSE) for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
