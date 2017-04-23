# jsdoc-sourcecode-tag

![jsdoc3](https://img.shields.io/badge/JSDoc3-plugin-blue.svg)
![license](https://img.shields.io/badge/License-MIT-orange.svg)

## What is this?

A JSDoc plugin that adds recognition to the @sourcecode tag for using his data in your publish theme.  
It can be used for demonstration part of codes in &lt;pre> element

More info about jsdoc and publish theme:  
- https://www.npmjs.com/package/jsdoc
- http://usejsdoc.org/
- http://usejsdoc.org/about-plugins.html

## Installing

```shell
npm install --save jsdoc-sourcecode-tag
# or using yarn cli
yarn add jsdoc-sourcecode-tag
```

## Usage

Add plugin to jsdoc conf.json (http://usejsdoc.org/about-configuring-jsdoc.html)

```json
{
    "plugins": ["./node_modules/jsdoc-sourcecode-tag/index"]
}
```

In your code

```js
/**
 * description
 * @const {Function}
 * @param {number} num
 * @returns {boolean}
 * @sourcecode
 */

const myFunction = function(num) {
	// some cool code here
};
```

In your publish theme data you will get `data.sourcecode`
- `lineno` - where it's start in your code
- `type` - definition type, alias of `data.meta.code.type`
- `value` - string with your code, start from `const myFun...` and to the end `...};`.

### tag value 

#### +{number}

Add lines after ending of documented code

```js
/**
 * Want to show const declaration
 * and same code part after that
 * @const {number}
 * @sourcecode +4
 */

const knockSeveralTimes = 10;
                                               // 1
for (let i = 1; i <= knockSeveralTimes; i++) { // 2
    console.log( `knock ${i}` );               // 3
}                                              // 4
```

#### |+{number}

It remove all lines of documented code and will start count from new line after

```js
/**
 * @name nowYouSeeMyLoop
 * @sourcecode |+3
 */
for (let i = 1; i <= knockSeveralTimes; i++) {  // 1
    console.log( `knock ${i}` );                // 2
}                                               // 3
```

## Tests

Sorry but here no tests yet.

## To Do

write tests and more examples

## Contributing

You're welcome - [issues](https://github.com/dutchenkoOleg/jsdoc-sourcecode-tag/issues) and [pulls](https://github.com/dutchenkoOleg/jsdoc-sourcecode-tag/pulls)

