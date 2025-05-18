<!-- Badges: -->
[![Contributions](https://img.shields.io/badge/contributions-welcome-orange?style=flat-square)](https://github.com/camponogaraviera/nvm-npm-yarn/pulls)

<!-- Title: -->
<div align='center'>
  <h1> SemVer + NVM + NPM + Yarn </h1>
</div>

# Table of Contents

- [Semantic Versioning (SemVer)](#semantic-versioning-semver)
- [Node Version Manager (NVM)](#node-version-manager-nvm)
- [Node Package Manager (NPM)](#node-package-manager-npm)
  - [Bump/Updating NPM](#bumpupdating-npm)
  - [Bump/Updating Node.js](#bumpupdating-nodejs)
  - [Creating a package.json file](#creating-a-packagejson-file)
  - [Creating a .gitignore file](#creating-a-gitignore-file)
  - [Installing NPM packages](#installing-npm-packages)
  - [Uninstalling NPM packages](#uninstalling-npm-packages)
  - [Listing installed dependencies](#listing-installed-dependencies)
  - [Viewing Package Info](#viewing-package-info)
  - [Checking for Releases (Current, Wanted, Latest)](#checking-for-releases-current-wanted-latest)
  - [Bump/Updating NPM packages](#bumpupdating-npm-packages)
  - [Start Project](#start-project)
  - [Environment Variables](#environment-variables)
- [Yarn Package Manager](#yarn-package-manager)

<!-- ################################################################ -->

# Semantic Versioning (SemVer)

Package versions follow the `Major.Minor.Patch` format:

- **Major**: Breaking changes (API might break).
- **Minor**: New features (API remains compatible).
- **Patch**: Bug fixes (no changes to the API).

## Versioning Symbols

- The caret (^) character allows updates within the same major version. 
- The tilde (~) character allows updates within the same minor version.

Examples:

```bash
"package": "^1.2.0"  # Allows 1.x.x (1.3.0, 1.4.0, etc.), but not 2.0.0. 
"package": "~1.2.0"  # Allows 1.2.x (1.2.0, 1.2.1, etc.), but not 1.3.0. 
"package": "1.0.0"   # Locks to exactly 1.0.0 (no updates allowed).
```

---

<!-- ################################################################ -->

# Node Version Manager (NVM)

NVM handles the installation and versioning of Node.js.

Note: prefer `Long-Term Support (LTS) versions` over Stable releases for production.

## Installing [Node.js](https://nodejs.org/en) with NVM

- First, install [Node Version Manager](https://github.com/nvm-sh/nvm) (NVM):
```bash
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
- Check installation:
```bash
command -v nvm 
```
- Install a specific version of Node.js:
```
nvm install <version>
```
- Or install the latest LTS release version of Node.js:
```bash
nvm install --lts
```
- Or install the latest stable version of Node.js:
```bash
nvm install node
```
- List Node.js installed versions:
```bash
nvm list
```
- Use a specific installed version of Node.js:
```bash
nvm use <version>
```
- Or use the latest LTS release version (recommended):
```bash
nvm use --lts
```
- Or use the latest stable version:
```bash
nvm use node
```

---

<!-- ################################################################ -->

# Node Package Manager (NPM) 

NPM handles the installation and versioning of package dependencies.

- NPM is shipped standard with Node.js:
```bash
node -v && npm -v
```

<!-- ################################################################ -->

## Bump/Updating NPM 

- Updating NPM to the latest stable version globally:
```bash
npm i -g npm@latest && npm -v
```

- Flags: `i` stands for install, and `-g` for global.

<!-- ################################################################ -->

## Bump/Updating Node.js

- Updating Node.js to a specific version (for example, to version 22.14.0):
```bash
npm i -g node@22.14.0 --force
```

<!-- ################################################################ -->

## Creating a `package.json` File

```bash
npm init --yes
```

<!-- ################################################################ -->

## Creating a `.gitignore` File

```bash
npm install -g gitignore && gitignore node
```

<!-- ################################################################ -->

## Installing NPM Packages

- Install all package dependencies from the `package.json` file:
```bash
npm i
```

- Install a Package as a Development Dependency:
```bash
npm i <dev-dependency> --save-dev
```

- Install a Package as a Production Dependency:
```bash
npm i <production-dependency> --save
```

<!-- ################################################################ -->

## Uninstalling NPM Packages

```bash
npm un <package_name>
```

<!-- ################################################################ -->

## Listing Installed Dependencies

```bash
npm list --depth=0
```

<!-- ################################################################ -->

## Viewing Package Info

```bash
npm view <package_name> dependencies
```

<!-- ################################################################ -->

## Checking for Releases (Current, Wanted, Latest)

```bash
npm outdated
```

<!-- ################################################################ -->

## Bump/Updating NPM Packages

- Updating a package to a specific version:
```bash
npm install <package_name>@<specific_version>
```

- To update all dependencies listed in `package.json` to the latest minor and patch releases respecting semver (e.g., ^1.2.3 -> ^1.x.x)
```bash
npm update  
```

- To update all dependencies listed in `package.json` to the latest versions ignoring semver (e.g., ^1.2.3 -> ^2.0.0) and installing them:
```bash
npm i -g npm-check-updates
ncu -u && npm i
```

<!-- ################################################################ -->

# Start Project

- Start the development server and reset the Metro bundler cache:
```bash
npm start -- --reset-cache
```

<!-- ################################################################ -->

## Environment Variables 

The following commands are intended for execution in a Terminal interface of a Linux-like system.

- To set an environment variable to development mode:
```bash
export NODE_ENV=development
```

- To set an environment variable to production mode:
```bash
export NODE_ENV=production
```

- To simulate a dynamic port assigned by the host:
```bash
export PORT=5000
```

- To unset the port:
```bash
unset NODE_ENV PORT
```

---

<!-- ################################################################ -->

# Yarn Package Manager 

Yarn is suitable for handling installation and versioning of package dependencies for React-based applications.

<!-- ################################################################ -->

## Installing Yarn

- Corepack (shipped by default with Node.js) is used to manage Yarn:
```bash
corepack enable
```

<!-- ################################################################ -->

## Bump/Updating Yarn

- [Updating Yarn](https://yarnpkg.com/getting-started/install#updating-yarn) to the latest stable version:
```bash
yarn set version stable && yarn -v
```

<!-- ################################################################ -->

## Creating a New Project

- Initializing a new project and upgrading it to Yarn V2+ (Berry):
```bash
yarn init -2
```

<!-- ################################################################ -->

## Creating a `package.json` file

```bash
yarn init --yes
```

<!-- ################################################################ -->

## Creating a `.gitignore` file

```bash
yarn add gitignore-parser && gitignore node
```

<!-- ################################################################ -->

## Installing Yarn Packages

- Install all package dependencies from the `package.json` file:
```bash
yarn install
```

- Install a package as a Development Dependency:
```bash
yarn add <dev-dependency> [--dev/-D]
```

- Install a package as a Production Dependency:
```bash
yarn add <production-dependency>
```

<!-- ################################################################ -->

## Uninstalling Yarn Packages

```bash
yarn remove <package_name>
```

<!-- ################################################################ -->

## Listing Installed Dependencies

- For old Yarn versions:
```bash
yarn list --depth=0
```

- For Yarn V2+ (Berry):
```bash
yarn info
```
or
```bash
yarn info --name-only
```

<!-- ################################################################ -->

## Viewing Package Info

```bash
yarn info <package_name>
```
or
```bash
yarn why <package_name>
```

<!-- ################################################################ -->

## Checking for Releases (Current, Range, Latest)

- For old Yarn versions:
```bash
yarn outdated
```

- For Yarn V2:
```bash
yarn upgrade-interactive
```

<!-- ################################################################ -->

## Bump/Updating Yarn Packages

- Updating a package to a specific version:
```bash
yarn add <package_name>@<specific_version>
```

- Selecting Yarn packages to update:
```bash
yarn upgrade-interactive
```

- Update everything to the latest versions within the range:
```bash
yarn up "*"
```

<!-- ################################################################ -->

## Peer Dependencies

- Identify and explain the peer dependencies of a project:
```bash
yarn explain peer-requirements
```

<!-- ################################################################ -->

## Start Project

- Start the development server and reset the Metro bundler cache:
```bash
yarn start --reset-cache
```

<!-- ################################################################ -->

## Environment Variables

The Yarn commands for setting, unsetting, and simulating environment variables are the same as for NPM.

---

# References

[1] https://github.com/nvm-sh/nvm

[2] https://docs.npmjs.com/cli/v10/commands

[3] https://www.npmjs.com/package/npm-check-updates

[4] https://nodejs.org/en/learn/getting-started/nodejs-the-difference-between-development-and-production

[5] https://en.wikipedia.org/wiki/Environment_variable
