<div align="center">
  <h2>Workflows</h2>
  <p>A collection of reusable GitHub Actions workflows for JavaScript and TypeScript projects.</p>
</div>

### What Does It Do?

**Workflows** provides standardized CI/CD workflows that you can plug into any JavaScript or TypeScript repository.

```yaml
name: Release

on:
  push:
    tags:
      - 'v*'

permissions:
  contents: write
  id-token: write

jobs:
  release:
    uses: arikchakma/workflows/.github/workflows/release-pnpm.yml@v1
    with:
      publish: true
      build: pnpm run build
    secrets: inherit
```

### Workflows

| Workflow                                                     | Description                             |
| ------------------------------------------------------------ | --------------------------------------- |
| [release-pnpm.yml](./.github/workflows/release-pnpm.yml)     | Release and publish packages using PNPM |
| [release-bun.yml](./.github/workflows/release-bun.yml)       | Release and publish packages using Bun  |
| [release-github.yml](./.github/workflows/release-github.yml) | Publish to GitHub Packages registry     |

See the [`examples/`](./examples) folder for sample configurations.

### Actions

| Action                            | Description                                    |
| --------------------------------- | ---------------------------------------------- |
| [setup-js](./setup-js/action.yml) | Sets up Node.js or Bun with dependency caching |

#### Setup Action Inputs

| Input                | Description                              | Default  |
| -------------------- | ---------------------------------------- | -------- |
| `package-manager`    | Package manager to use (`pnpm` or `bun`) | `pnpm`   |
| `node-version`       | Node.js version (for pnpm)               | `lts/*`  |
| `bun-version`        | Bun version (for bun)                    | `latest` |
| `auto-install`       | Automatically install dependencies       | `true`   |
| `no-frozen-lockfile` | Disable frozen lockfile                  | `false`  |

### Acknowledgements

This project is inspired by [sxzz/workflows](https://github.com/sxzz/workflows) by [Kevin Deng](https://github.com/sxzz). Thank you for the excellent reference implementation.

### Contributing

Feel free to submit pull requests, create issues, or spread the word.

### License

MIT &copy; [Arik Chakma](https://x.com/imarikchakma)
