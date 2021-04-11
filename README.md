[![npm](https://img.shields.io/npm/dt/rollup-plugin-external-assets)](https://www.npmjs.com/package/rollup-plugin-external-assets)
[![npm](https://img.shields.io/npm/v/rollup-plugin-external-assets)](https://www.npmjs.com/package/rollup-plugin-external-assets)
[![Build Status](https://travis-ci.com/soufyakoub/rollup-plugin-external-assets.svg?branch=master)](https://travis-ci.com/soufyakoub/rollup-plugin-external-assets)
[![codecov](https://codecov.io/gh/soufyakoub/rollup-plugin-external-assets/branch/master/graph/badge.svg)](https://codecov.io/gh/soufyakoub/rollup-plugin-external-assets)
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)][1]

# rollup-plugin-external-assets
> A rollup plugin to make assets external but include them in the output.

:memo: Since library bundling is the primary use of this plugin, dynamic imports are not supported. Use at your own risk.

## Installation

Via [npm][2]

```sh
npm install --save-dev rollup-plugin-external-assets
```

Via [yarn][3]

```sh
yarn add -D rollup-plugin-external-assets
```

## Usage

```javascript
import nodeResolve from "@rollup/plugin-node-resolve";
import externalAssets from "rollup-plugin-external-assets";

export default {
	input: "src/index.js",
	output: {
		file: "dist/index.js",
		format: "es",
		sourcemap: true,
	},
	plugins: [
		nodeResolve(),
		externalAssets("assets/*.png"),
	],
};
```

## API

```typescript
function externalAssets(pattern: string | RegExp | (string | RegExp)[]);
```

### pattern

`string | RegExp | (string | RegExp)[]`

A picomatch pattern, or array of patterns, which correspond to assets the plugin should operate on.

```javascript
// Operate on images located in the ./assets directory.
externalAssets("assets/**/*.jpg");

// Operate on images located in the ./assets directory.
// and all stylesheet files.
externalAssets(["assets/**/*.{jpg,png}", /\.(css|scss)$/]);
```

## Contributing

### Prerequisites
- [nodejs][4]
- [npm][2]

### Getting Started

After cloning this repo, ensure dependencies are installed by running:

```sh
npm install
```

Then to build the final bundle:

```sh
npm run build
```

### Tests

To run tests:

```sh
npm test
```

Note that rollup may emit warnings for unspecified options, or for some other reasons.
I made sure they are ignored with the `ROLLUP_WARNINGS` environment variable in the npm test script.

If you want to see all the warnings when running tests, use this command instead:

```sh
npm run test:warn
```

Coverage report is located in `tests/coverage`.
You might want to review it in your browser, and for example,
write tests for non-covered blocks, or remove them if they're useless.

To run tests and update snapshots, pass the `-u` flag to [jest][8] through the `test` (or `test:warn`) npm script:

```sh
npm test -- -u
```

### Commiting changes

Please follow the [conventional commits][5] specification, because [semantic-release][6] is used to automate the whole package release workflow including: determining the next version number, generating the release notes and publishing the package.

## License

[MIT][1]

[1]: LICENSE
[2]: https://npmjs.org/
[3]: https://yarnpkg.com
[4]: https://nodejs.org
[5]: https://www.conventionalcommits.org/en/v1.0.0/
[6]: https://github.com/semantic-release/semantic-release
[7]: https://github.com/concordancejs/concordance/issues/68
[8]: https://jestjs.io/
