# @taktikorg/reiciendis-illum <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

[![browser support][testling-svg]][testling-url]

An ES5 spec-compliant `Array.prototype.every` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the proposed [spec](https://www.ecma-international.org/ecma-262/6.0/).

Because `Array.prototype.every` depends on a receiver (the “this” value), the main export takes the array to operate on as the first argument.

## Example

```js
var every = require('@taktikorg/reiciendis-illum');
var assert = require('assert');

assert.equal(true, every([1, 1, 1], function (x) { return x === 1; }));
assert.equal(false, every([1, 0, 1], function (x) { return x === 1; }));
```

```js
var every = require('@taktikorg/reiciendis-illum');
var assert = require('assert');
/* when Array#every is not present */
delete Array.prototype.every;
var shimmedEvery = every.shim();
assert.equal(shimmedEvery, every.getPolyfill());
var arr = [1, 2, 3];
var lessThan4 = function (x) { return x < 4; };
assert.deepEqual(arr.every(lessThan4), every(arr, lessThan4));
```

```js
var every = require('@taktikorg/reiciendis-illum');
var assert = require('assert');
/* when Array#every is present */
var shimmedEvery = every.shim();
assert.equal(shimmedEvery, Array.prototype.every);
assert.deepEqual(arr.every(lessThan4), every(arr, lessThan4));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/@taktikorg/reiciendis-illum
[npm-version-svg]: https://versionbadg.es/taktikorg/reiciendis-illum.svg
[deps-svg]: https://david-dm.org/taktikorg/reiciendis-illum.svg
[deps-url]: https://david-dm.org/taktikorg/reiciendis-illum
[dev-deps-svg]: https://david-dm.org/taktikorg/reiciendis-illum/dev-status.svg
[dev-deps-url]: https://david-dm.org/taktikorg/reiciendis-illum#info=devDependencies
[testling-svg]: https://ci.testling.com/taktikorg/reiciendis-illum.png
[testling-url]: https://ci.testling.com/taktikorg/reiciendis-illum
[npm-badge-png]: https://nodei.co/npm/@taktikorg/reiciendis-illum.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@taktikorg/reiciendis-illum.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@taktikorg/reiciendis-illum.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@taktikorg/reiciendis-illum
[codecov-image]: https://codecov.io/gh/taktikorg/reiciendis-illum/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/taktikorg/reiciendis-illum/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/taktikorg/reiciendis-illum
[actions-url]: https://github.com/taktikorg/reiciendis-illum/actions
