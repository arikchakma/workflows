# arikchakma/workflows

Reusable GitHub Actions workflows for publishing packages with PNPM and Bun.

## Features

- Release workflows for both **PNPM** and **Bun** package managers
- Publish to **NPM** or **GitHub Packages** registry
- Composite setup action with caching support
- Automatic changelog generation

## Included Workflows

- **Release (PNPM)**: Publish packages using PNPM to NPM registry
- **Release (Bun)**: Publish packages using Bun to NPM registry
- **Release (GitHub)**: Publish packages to GitHub Packages registry (supports both PNPM and Bun)

## Usage

Reference a workflow in your project's `.github/workflows/*.yml`:

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

See the [`examples/`](./examples) folder for sample configurations:

- [Release (PNPM)](./examples/release-pnpm.yml)
- [Release (Bun)](./examples/release-bun.yml)
- [Release (GitHub Packages)](./examples/release-github.yml)

## Actions

- [`setup-js/action.yml`](./setup-js/action.yml): Sets up Node.js/Bun and installs dependencies

### Setup Action Inputs

| Input                | Description                              | Default  |
| -------------------- | ---------------------------------------- | -------- |
| `package-manager`    | Package manager to use (`pnpm` or `bun`) | `pnpm`   |
| `node-version`       | Node.js version (for pnpm)               | `lts/*`  |
| `bun-version`        | Bun version (for bun)                    | `latest` |
| `auto-install`       | Automatically install dependencies       | `true`   |
| `no-frozen-lockfile` | Disable frozen lockfile                  | `false`  |

## Contributing

Feel free to submit pull requests, create issues, or spread the word.

## Acknowledgements

This project is inspired by [sxzz/workflows](https://github.com/sxzz/workflows) by [Kevin Deng](https://github.com/sxzz). Thank you for the excellent reference implementation.

## License

MIT &copy; [Arik Chakma](https://x.com/imarikchakma)
