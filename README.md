# GitHub Smart Changelog Generator 🚀
[![License: MIT](https://img.shields.io/badge/License-MIT-blue)](LICENSE) 
[![GitHub Issues](https://img.shields.io/github/issues/uncodelab/github-smart-changelog-generator?label=Public%20Issues)](https://github.com/uncodelab/github-smart-changelog-generator/issues) 

**This GitHub Actions workflow, `update-changelog.yml`, automates the creation of a categorized changelog based on commit messages.** It triggers when you publish a release (e.g., tagging v1.0.0) and updates a `CHANGELOG.md` file in a target repository. The workflow is designed to be reusable and customizable for any project following a conventional commit style.

**Purpose**: The **GitHub Smart Changelog Generator** simplifies release documentation by categorizing commits into sections like New Features, Bug Fixes, Documentation, etc., making it ideal for open-source projects or teams that want clear, automated release notes.

---

## Requirements 📋

Before using the `update-changelog.yml` workflow, ensure your repository meets these prerequisites:
- A GitHub repository with release tags (e.g., `v1.0.0`) to trigger the workflow.
- A target repository where the `CHANGELOG.md` will be updated (e.g., `your-org/your-repo`).
- A GitHub Personal Access Token (PAT) with repo scope (read/write access to the target repository) stored as a GitHub Secret named `REPO_TOKEN`.
- Commit messages following the Conventional Commits format (e.g., `feat: add login`, `fix: resolve bug`) for proper categorization.
- GitHub Actions enabled in your repository (enabled by default for public repositories).

---

## Installation 🛠️

To use the **GitHub Smart Changelog Generator** workflow, download the `update-changelog.yml` file and add it to your repository’s `.github/workflows/` directory.

### Steps

1. **Download the Workflow**:
   - Navigate to `update-changelog.yml`.
   - Click Raw, then save the file (e.g., right-click and select "Save As").
2. **Add to Your Repository**:
   - Create the .github/workflows/ directory in your repository:
   ```bash
   mkdir -p .github/workflows
   ```
   - Move or copy `update-changelog.yml` to `.github/workflows/`:
   ```bash
   cp update-changelog.yml .github/workflows/
   ```
3. **Configure the Workflow**:
   - Update the repository field in the Checkout target repo step to your target repository (e.g., `your-org/your-repo`).
   - Optionally, replace `issues-repo` with a different directory name (e.g., `target-repo`) for the checkout path.
   - Ensure your commit messages follow the Conventional Commits format (e.g., `feat: add feature`, `fix: resolve issue`).
4. **Set Up Secrets**:
   - Go to your repository’s **Settings > Secrets and variables > Actions > Secrets**.
   - Add a secret named `REPO_TOKEN` with a PAT that has read/write access to the target repository.
5. **Test the Workflow**:
   - Create a release in your repository via GitHub’s Releases page or by pushing a tag:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
   - The workflow will run, updating the `CHANGELOG.md` in the target repository.

---

## Features ✨

The **Automated Changelog Creation**: workflow provides these key functionalities:
- **Automated Changelog Creation**: Generates a categorized changelog based on commit messages when a release is published, supporting both the same repository and a separate target repository.
- **Conventional Commits Support**: Categorizes commits with prefixes like feat:, fix:, docs:, etc., into sections (e.g., `New Features`, `Bug Fixes`).
- **Noise Commit Filtering**: Skips irrelevant commits, such as those containing phrases like "version bump," "merge branch," or "update changelog for," to reduce changelog clutter.
- **Target Repository Updates**: Updates the CHANGELOG.md in a specified repository (e.g., `your-org/your-repo`).
- **Flexible Commit Parsing**:
  - Skips irrelevant commits (e.g., those containing “version bump” or “merge branch”).
  - Handles uncategorized commits in a separate Uncategorized section.
- **Version and Date Tracking**: Adds release version (e.g., 1.0.0) and date to the changelog.
- **Git Integration**: Automatically commits and pushes the updated `CHANGELOG.md` using GitHub Actions.

---

## Usage 💻

1. **Trigger the Workflow**:
   - Publish a release in your repository (e.g., create a tag like v1.0.0).
   - The workflow runs automatically, parsing commits and updating the `CHANGELOG.md` in the target repository.
2. **Example Output**: The resulting `CHANGELOG.md` looks like:
   ```markdown
   # Changelog

   ## [1.0.0] - 2025-07-09

   ### New Features
   - Add user authentication
   - Implement login page

   ### Bug Fixes
   - Resolve crash on startup

   ### Uncategorized
   - Update dependencies
   ```

---

## Customization 🔧

You can modify `update-changelog.yml` to suit your needs:
- **Change the Target Repository**: Update the `repository` field in the Checkout target repo step.
- **Modify Categories**: Edit the `categories` array in the **Generate categorized changelog** step (e.g., add `[security]="Security Updates"`).
- **Adjust Skip Patterns**: Update the `skip_patterns` array to ignore additional commit messages.
- **Custom Commit Range**: Modify the `git log` command to include different commits.

---

## Maintenance ⬆️

- **Dependencies**: The workflow uses `actions/checkout@v4`, maintained by GitHub. Check for updates (e.g., `@v5`) or pin to a specific version (e.g., `actions/checkout@4.1.1`) for stability.
- **Workflow Updates**: Check this repository’s releases for updates to `update-changelog.yml`.
- **Custom Versions**: If you modify the workflow, consider renaming it (e.g., `changelog-generator.yml`) to avoid conflicts with future updates.

## Changelog 📜

The `update-changelog.yml` workflow generates changelogs for target repositories. See the [CHANGELOG.md](https://github.com/uncodelab/github-smart-changelog-generator/blob/main/CHANGELOG.md) file for a detailed history of updates and changes to GitHub Smart Changelog Generator.

---

## Issue Tracker 🐞

[![GitHub Issues](https://img.shields.io/github/issues/uncodelab/github-smart-changelog-generator?label=Public%20Issues)](https://github.com/uncodelab/github-smart-changelog-generator/issues)

All bug reports and feature requests are managed through our public issue tracker.

Encounter a bug or have a feature idea? File it at [GitHub Smart Changelog Generator Issues](https://github.com/uncodelab/github-smart-changelog-generator/issues):
- **Bugs**: Provide steps to reproduce, expected vs. actual behavior, and environment details..
- **Features**: Describe the feature and its benefits.

**Tip**: Check existing issues to avoid duplicates.

---

## Project Status 🏗️

Actively maintained with regular updates.

---

## License 📝

[![License: MIT](https://img.shields.io/badge/License-MIT-blue)](LICENSE) 

This workflow is licensed under the MIT License. You are free to use, modify, and distribute it, subject to the license terms.
**See full [LICENSE](LICENSE) for legal terms of use.**  

---

*Copyright (c) 2025 uncodelab. All rights reserved.*