# Release

This project uses [Changesets](https://github.com/changesets/changesets) for
versioning and release notes. Run these commands from the repository root after
installing dependencies with `npm ci`.

## Add a changeset

For a user-facing package change, run the locally installed Changesets CLI:

```sh
npm exec -- changeset
```

The CLI selects this package and asks for a version bump and changelog summary.

Choose `patch` for backward-compatible fixes, `minor` for backward-compatible
features, and `major` for breaking changes. Write a summary for package users.

Documentation-only, test-only, and internal refactor PRs usually do not need a
changeset unless they accompany a release-worthy behavior change.

### Without an interactive TTY

Create a Markdown file in `.changeset/` with YAML front matter identifying the
package and version bump. Choose an unused, descriptive filename for each change.

```sh
PACKAGE_NAME=$(node -p "require('./package.json').name")
cat > .changeset/package-fix.md <<EOF
---
"$PACKAGE_NAME": patch
---

Describe the user-facing fix here.
EOF
```

Replace the example summary with the actual change and select the appropriate
version bump. Read the package name from `package.json` as shown above.

Validate the changeset without versioning or publishing:

```sh
npm exec -- changeset status
```

Commit the changeset with the implementation and push the branch normally:

```sh
git add .changeset
git commit -m "chore: add changeset"
git push origin HEAD
```

## Automated release flow

The [release workflow](.github/workflows/release.yml) runs on pushes to `main`.
When pending changesets exist, Changesets creates or updates a release PR with
version bumps and changelog entries. Review that PR and merge it when ready.
The workflow then publishes the versioned packages to npm.

The workflow needs permission to create release PRs. In repository
**Settings > Actions > General > Workflow permissions**, enable
**Allow GitHub Actions to create and approve pull requests**. The workflow
declares its own token permissions; enabling the global read/write default is
not required. Publishing also requires the workflow's configured npm credentials.

## Manual release commands

The workflow normally runs these scripts. For a deliberate manual release,
first ensure the intended changes are merged and checks pass:

```sh
npm run version
```

Review and commit the generated version and changelog changes before publishing:

```sh
npm run release
```

The release command publishes to npm; it is not a validation command.
