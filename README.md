# check-peer-deps

[![GitHub License](https://img.shields.io/github/license/sounisi5011/check-peer-deps.svg)][github-license]
[![Build Status](https://travis-ci.com/sounisi5011/check-peer-deps.svg?branch=master)](https://travis-ci.com/sounisi5011/check-peer-deps)

[github-license]: https://github.com/sounisi5011/check-peer-deps/blob/master/LICENSE

Verifies that the `peerDependency` requirements of all top level dependencies
are satisfied.

## Forked package

This package is a fork of [Arcanemagus/check-peer-deps](https://github.com/Arcanemagus/check-peer-deps).
The main purpose is the resolve of Issue [#11](https://github.com/Arcanemagus/check-peer-deps/issues/11).

## Installation

You can install this on your system with:

```sh
npm install sounisi5011/check-peer-deps
```

Please note that this utility requires `npm` to be available.

## Usage

Simply change into the directory of the project you wish to check the
`peerDependencies` of and run the program.

```sh
> cd foobar
> check-peer-deps
```

If the minimum versions of all your top level `peerDependencies` are satisfied
then there will be no output, otherwise you will see something similar to this:

```
  > check-peer-deps
  A dependency satisfying eslint-config-airbnb-base's peerDependency of 'eslint@^4.9.0' was not found!
  Current: eslint@^4.6.0
  Package dependencies can satisfy the peerDependency? Yes
```

This tells you that `eslint-config-airbnb-base` is requiring `eslint@^4.9.0` as
a `peerDependency`, but the project currently only specifies `eslint@^4.6.0`,
allowing a potential issue to arise if `eslint@4.6.0` was installed and not
updated before installing. The output also tells you that although the
_minimum_ allowed version is too low, the _maximum_ allowed version does
satisfy the `peerDependencies` requirement.


If you use resolutions section in your package.json file in order to resolve some unmet peer dependencies
and want the program to take it into the account run it with include-resolutions option:

```
> check-peer-deps --include-resolutions=true
```

Read more about resolutions: https://yarnpkg.com/lang/en/docs/selective-version-resolutions/
