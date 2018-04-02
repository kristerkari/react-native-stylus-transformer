# react-native-stylus-transformer

[![NPM version](http://img.shields.io/npm/v/react-native-stylus-transformer.svg)](https://www.npmjs.org/package/react-native-stylus-transformer)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)

Load [Stylus](https://github.com/stylus/stylus) files to [react native style objects](https://facebook.github.io/react-native/docs/style.html).

> This transformer can be used together with [React Native CSS modules](https://github.com/kristerkari/react-native-css-modules).

## Usage

### Step 1: Install

```sh
yarn add --dev react-native-stylus-transformer stylus
```

### Step 2: Configure the react native packager

Add this to your `rn-cli.config.js` (make one if you don't have one already):

```js
module.exports = {
  getTransformModulePath() {
    return require.resolve("react-native-stylus-transformer");
  },
  getSourceExts() {
    return ["styl"];
  }
};
```

## How does it work?

Your `App.styl` file might look like this:

```css
.myClass {
  color: blue;
}
.myOtherClass {
  color: red;
}
```

When you import your stylesheet:

```js
import styles from "./App.styl";
```

Your imported styles will look like this:

```js
var styles = {
  myClass: {
    color: "blue"
  },
  myOtherClass: {
    color: "red"
  }
};
```

You can then use that style object with an element:

```jsx
<MyElement style={styles.myClass} />
```
