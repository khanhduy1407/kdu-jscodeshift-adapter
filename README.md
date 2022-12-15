# kdu-jscodeshift-adapter

Run [jscodeshift](https://github.com/facebook/jscodeshift) on Kdu single file components

## Install

```
npm install kdu-jscodeshift-adapter -D
```

## Usage

The instructions below assume you're familiar with [jscodeshift](https://github.com/facebook/jscodeshift).

### Run a codemod on some `.js` and/or `.kdu` files

|When transforming|`fileInfo.source` will be|
|-----------------|-------------------------|
|`.js`            | the contents of the file|
|`.kdu`           | the contents of `<script>`|

The source file will be updated appropriately based on the return value of your `transform()`.

*If `.kdu` file doesn't have a `<script>`, your `transform()` will not be called and the source file will not be changed.*

#### 1. Create wrapped transform function

```js
// my-transform.js
const adapt = require('kdu-jscodeshift-adapter');
const someCodemod = require('some-codemod');

module.exports = adapt(someCodemod);
```

#### 2. Run jscodeshift

```
$ jscodeshift <path> -t my-transform.js --extensions kdu,js
```

See [jscodeshift readme](https://github.com/facebook/jscodeshift#usage-cli) for more info on jscodeshift CLI.

## License

MIT