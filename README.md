# bioc-modules
Prototype central repository for Nextflow modules created through BiocJobs.

## Process

- Action in source repo sends a dispatch with metadata (repo, package name, version, commit SHA) to bioc-modules upon completion of biocjobs actions (needs standardising).
  - Requires a token to dispatch to bioc-modules.
- Upon receiving dispatch, bioc-modules
  - Checks out both repos
  - Copies changed .nf files in source-repo/wrappers into bioc-modules/<package name>/<module name>.nf, and deletes removed files.
  - Commits changes and creates a pull request under a new branch called [sync-<package name>].
  - If no changes are detected, exist without creating a new PR.
