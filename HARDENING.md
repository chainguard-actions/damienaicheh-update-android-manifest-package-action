<!-- markdownlint-disable -->

# Hardening Report: damienaicheh--update-android-manifest-package-action/v1.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **damienaicheh--update-android-manifest-package-action/v1.0.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow files reference actions by mutable tags instead of full 40-character SHA commit hashes, making them vulnerable to supply-chain attacks if the tag is moved. Failing references: 'actions/checkout@v2' (tag, not SHA) in both sample.yml and versions.yml; 'damienaicheh/update-android-manifest-package-action@v1.0.0' (tag, not SHA) in sample.yml.

Locations:

- `.github/workflows/sample.yml:17`
- `.github/workflows/sample.yml:21`
- `.github/workflows/versions.yml:17`

### missing-permissions (severity: medium)

Neither workflow file defines a top-level 'permissions:' key, and no job within either file defines job-level permissions. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/sample.yml:1`
- `.github/workflows/versions.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed both workflow files (.github/workflows/sample.yml and .github/workflows/versions.yml):
1. unpinned-uses: Pinned 'actions/checkout@v2' to full SHA '0717577d45739eb3c851188b29f50ed6c0b2194e' in both files; pinned 'damienaicheh/update-android-manifest-package-action@v1.0.0' to full SHA '87f94e081b3cece7cee7841093e878fdc589028a' in sample.yml. Original tags preserved as inline comments.
2. missing-permissions: Added 'permissions: {}' at the top level of both workflow files to enforce least privilege on the GITHUB_TOKEN.

