# **NPM Cheat Sheet**

## **Table of Contents**

1. [Versioning](#versioning "View")
   1. [Version Ranges](#version-prefixes "View")
1. [Node Executables](#node-executables "View")
   1. [NPX](#npx "View")
1. [Configuration](#configuration "View")
   1. [Environment Variables](#environment-variables "View")
   1. [Npmrc Files](#npmrc-files "View")
1. [Registries](#registries "View")

## **Versioning**

The project uses [SemVer](https://semver.org "Visit").

Format: `<major>`**`.`**`<minor>`**`.`**`<patch>`

> _Only use positive integers._

- Optional prerelease postfix starts with "**`-`**", and is interpreted as dot separated values:
  - eg. `0.0.1-alpha.1`
- Optional build metadata postfix starts with "**`+`**", and is interpreted as dot separated values:
  - eg. `0.0.1-alpha.1+debug.1`

| scenario                                  | increment |
| :---------------------------------------- | :-------- |
| backward compatible bug fixes             | patch     |
| backward compatible new features          | minor     |
| changes that break backward compatibility | major     |

### **Version Ranges**

You can specify what update types your project can accept from dependencies in your `package.json` file.

| version range | short | placeholder | prefix   | prefix name              |
| :------------ | :---- | :---------- | :------- | :----------------------- |
| all patch     | `1.0` | `1.0.x`     | `~1.0.0` | approximately equivalent |
| all minor     | `1`   | `1.x`       | `^1.0.0` | compatible               |
| all major     | `*`   | `x`         | -        | -                        |

> _NPM `install` will replace `*` version in `package.json` with a compatible current version._

## **Node Executables**

A package can provide one single, or multiple executables through its `package.json`:

```json
{
  "bin": {
    "<executable>": ".dist/index.js"
  },
  "man": [".man/<executable>.1"]
}
```

> _For this to work, the distributable `js` file(s) must start with the following [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix) "Visit"):\_
>
> _`#!/usr/bin/env node`_

Upon installing, `npm` will create wrappers for different shells (bash, Command Line, PowerShell) in the `node_modules/.bin` directory:

```
node_modules/
  .bin/
    <executable>
    <executable>.cmd
    <executable>.ps1
```

When running local `npm` scripts, the project's `node_modules/.bin` directory will be appended to the system's `$PATH` variable in the node environment (while globally installed package's `.bin` directory is already present in `$PATH`).

### **NPX**

Part of `npm`, `npx` is a tool for running package executables. First it looks into the local `node_modules` folder for the package, then for global installation, and finally if neither was found it will download and run the package (without having it installed globally).

```shell
$ npx cowsay hello!
```

> _`npx` can also execute a package from an URL, e.g. from a GitHub repository / gist:_
>
> _`$ npx https://gist.github.com/<user>/<gist-id>`_

## **Configuration**

Npm configuration [documentation](https://docs.npmjs.com/cli/using-npm/config "Visit").

Notable configurations:

- `--dry-run`:
  - Npm doesn't make any changes, only reports what it would have done.
- `--depth`:
  - The depth to go when recursing packages for `npm ls`.
- `--global`:
  - Packages will be installed into the `prefix` folder instead of the current working directory.
- `--engine-strict`:
  - Npm will refuse to install any package that is not compatible with the current Node.js version.
- `--fund=false`:
  - Display dependencies looking for funding at the end of `npm install`.
- `--progress=false`:
  - Display progress bar during time intensive operations.
- `--json`:
  - Output JSON data instead normal output.
- `--node-options=<options>`:
  - Options to pass through to Node.js via the `NODE_OPTIONS` environment variable.
- `--registry=<registry>`:
  - The base URL of the npm registry.
  - Default: `https://registry.npmjs.org/`
- `--update-notifier=false`:
  - Suppress the update notification when using an older version of npm.

### **Environment Variables**

- Environment variables that start with `npm_config_` will be interpreted as a configuration parameter.
- You need to use underscores instead of dashes, so `--allow-same-version` would become `npm_config_allow_same_version=true`.

```shell
# *nix
$ NODE_OPTIONS="--max-old-space-size=8192" node --print "v8.getHeapStatistics()"

# PowerShell
$ $Env:NODE_OPTIONS="--max-old-space-size=8192"; node --print "v8.getHeapStatistics()"; $Env:NODE_OPTIONS=$null
```

### **Npmrc Files**

- Per-project configuration: `/path/to/project/.npmrc`
- Per-user configuration: `~/.npmrc` (by default)
  - Configurable via CLI option `--userconfig`
  - Configurable via environment variable `$NPM_CONFIG_USERCONFIG`
- Global configuration file: `$PREFIX/etc/npmrc` (by default)
  - Configurable via CLI option `--globalconfig`
  - Configurable via environment variable `$NPM_CONFIG_GLOBALCONFIG`
- Npm's built-in configuration file: `/path/to/npm/npmrc`

## **Registries**

You can set the global registry:

```shell
$ npm set registry https://<registry-url>:<registry-port>/
```

You can pass a `--registry` flag when needed:

```shell
$ npm install --registry https://<registry-url>:<registry-port>/ @<scope>/<package>@<version>
```

You can define registry entries in your `.npmrc` also, either for project-wide, or scope-based usage:

```conf
registry=https://<registry-url>:<registry-port>/
@<scope>:registry=https://<registry-url>:<registry-port>/
```

> _Global settings are stored in your `~/.npmrc` file._

##

---

_©2020-2023 Barnabas Bucsy - All rights reserved._
