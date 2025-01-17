Forked from upstream with the following changes: https://github.com/azz/eslint-plugin-monorepo/compare/master...jdb8:master

- https://github.com/azz/eslint-plugin-monorepo/pull/21
- https://github.com/azz/eslint-plugin-monorepo/pull/29

If these changes are merged to `eslint-plugin-monorepo`, this fork can be deleted.

Until then, this fork can be installed via:

```bash
yarn add -D @jdb8/eslint-plugin-monorepo
```

or

```bash
npm install --save-dev @jdb8/eslint-plugin-monorepo
```

Unfortunately, any references to `monorepo/*` rules (such as in `eslint-ignore` comments) will have to be updated to point to `@jdb8/monorepo/*` temporarily. If anyone knows of a way to avoid this when forking an eslint plugin (via some kind of rule aliasing?) please reach out!

The original README is included below.

---

# `eslint-plugin-monorepo`

[![Travis](https://img.shields.io/travis/azz/eslint-plugin-monorepo.svg?style=flat-square)](https://travis-ci.org/azz/eslint-plugin-monorepo)
[![Prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)
[![npm](https://img.shields.io/npm/v/eslint-plugin-monorepo.svg?style=flat-square)](https://npmjs.org/eslint-plugin-monorepo)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg?style=flat-square)](https://github.com/semantic-release/semantic-release)
[![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](LICENSE)

A collection of ESLint rules for enforcing import rules in a monorepo. Supports:

- [Lerna](https://github.com/lerna/lerna)
- [Yarn workspaces](https://yarnpkg.com/lang/en/docs/workspaces/)

## Configuration

Use the `"recommended"` configuration:

```json
// .eslintrc.json
{
  "extends": ["plugin:monorepo/recommended"]
}
```

Or enable rules manually:

```json
// .eslintrc.json
{
  "plugins": ["monorepo"],
  "rules": {
    "monorepo/no-internal-import": "error",
    "monorepo/no-relative-import": "error"
  }
}
```

## Rules

### `monorepo/no-internal-import`

Forbids importing specific files from a monorepo package.

```js
// Bad
import 'module/src/foo.js';

// Good
import { foo } from 'module';
```

### `monorepo/no-relative-import` (fixable)

Forbids importing other packages from the monorepo with a relative path.

```js
// Bad
import module from '../module';

// Good
import module from 'module';
```
