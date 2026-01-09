---
name: changelog
description: Produces and updates the project's CHANGELOG.md file following Keep a Changelog 1.1.0 standards. Use when adding release notes, documenting changes, or preparing for a version release.
license: MIT
compatibility: opencode
metadata:
  audience: maintainers
  workflow: github
---

Before using this skill:

1. **Run the test suite first** - Use the @tester subagent to run the entire test suite. This is mandatory before continuing with the changelog skill.
2. **Abort if tests fail** - If any tests fail, DO NOT create/update the CHANGELOG.md file. Report the failure and stop immediately.

When managing the changelog:
1. **Analyze git history** to understand what changed:
    - Use `git tag --sort=-v:refname | head -1` to identify the last released version
    - Use `git log` to review recent commits since last release/tag
    - Use `git diff` to examine actual code changes
    - Examine commit messages for context about changes
    - Review file changes to understand scope and impact

2. **Interpret changes** and map them to user-facing impact:
    - Read the actual code diffs to understand what changed
    - Translate technical changes into user-friendly descriptions
    - Identify breaking changes, new features, bug fixes, etc.
    - Group related commits into single changelog entries
    - Focus on "why it matters" not "what code changed"
    - Use present tense

3. **Categorize changes** under appropriate headings:
    - `Added` - New features
    - `Changed` - Changes to existing functionality
    - `Deprecated` - Soon-to-be removed features
    - `Removed` - Removed features
    - `Fixed` - Bug fixes
    - `Security` - Vulnerability fixes

4. **Follow Keep a Changelog 1.1.0 format**:
    - Use `CHANGELOG.md` at project root
    - List changes in reverse chronological order (newest first)
    - Use ISO 8601 date format (YYYY-MM-DD)
    - Maintain an `[Unreleased]` section for upcoming changes

5. **Version format**:
   ```markdown
   ## [Version] - YYYY-MM-DD
   ### Category
   - Change description
   ```

6. **Key principles**:
    - Write for humans, not machines
    - Focus on notable changes that impact users
    - Make versions linkable
    - Use clear, concise language
    - Avoid commit log diffs - translate to user benefit
    - Clearly indicate breaking changes

7. **When updating**:
    - Add new changes to `[Unreleased]` section
    - When releasing, rename `[Unreleased]` to version with date
    - Create new empty `[Unreleased]` section at top
    - Link versions to git comparisons if possible
