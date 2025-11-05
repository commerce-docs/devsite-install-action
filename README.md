# devsite-install-action

A composite GitHub action to setup Node.js, configure Yarn, and install
dependencies for the Adobe Commerce DevSite projects based on Gatsby.

## Description

This action streamlines the setup process for Node.js projects by:

- Setting up Node.js using a version file (`.nvmrc`)
- Configuring Yarn caching for faster CI/CD workflows
- Enabling Corepack for Yarn package manager
- Installing project dependencies with `yarn install`

## Inputs

### `node-version-file`

**Required:** Yes

Path to the `.nvmrc` file that specifies the Node.js version to use.

**Example:** `.nvmrc`

### `cache-dependency-path`

**Required:** Yes

Path to the `yarn.lock` file for dependency caching.

**Example:** `yarn.lock`

## Usage

```yaml
- name: Setup Node.js and install dependencies
  uses: commerce-docs/devsite-install-action@main
  with:
    node-version-file: '.nvmrc'
    cache-dependency-path: 'yarn.lock'
```

### Monorepo example

For monorepos with multiple `yarn.lock` files:

```yaml
- name: Setup Node.js and install dependencies
  uses: commerce-docs/devsite-install-action@main
  with:
    node-version-file: '.nvmrc'
    cache-dependency-path: 'yarn.lock'
```

## What it does

1. **Setup Node.js** - Configures the Node.js environment using
   `actions/setup-node@v6` with the version specified in your `.nvmrc` file
2. **Enable Yarn caching** - Sets up dependency caching to speed up
   subsequent workflow runs
3. **Enable Corepack** - Activates Corepack to manage the Yarn package
   manager
4. **Install dependencies** - Runs `yarn install` with immutable installs
   disabled

## License

This project is licensed under the Apache License 2.0 - see the
[LICENSE](LICENSE) file for details.
