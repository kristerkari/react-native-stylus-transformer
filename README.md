# react-native-stylus-transformer [![NPM version](http://img.shields.io/npm/v/react-native-stylus-transformer.svg)](https://www.npmjs.org/package/react-native-stylus-transformer) [![Downloads per month](https://img.shields.io/npm/dm/react-native-stylus-transformer.svg)](http://npmcharts.com/compare/react-native-stylus-transformer?periodLength=30) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)

Use [Stylus](https://github.com/stylus/stylus) to style your React Native apps.

Behind the scenes the `.styl` files are transformed to [react native style objects](https://facebook.github.io/react-native/docs/style.html) (look at the examples).

> This transformer can be used together with [React Native CSS modules](https://github.com/kristerkari/react-native-css-modules).

## How does it work?

Your `App.styl` file might look like this:

```css
.myClass {
  color: blue;
}
.myOtherClass {
  color: red;
}
.my-dashed-class {
  color: green;
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
  },
  "my-dashed-class": {
    color: "green"
  }
};
```

You can then use that style object with an element:

**Plain React Native:**

```jsx
<MyElement style={styles.myClass} />

<MyElement style={styles["my-dashed-class"]} />
```

**React Native CSS modules using [className](https://github.com/kristerkari/babel-plugin-react-native-classname-to-style) property:**

```jsx
<MyElement className={styles.myClass} />

<MyElement className={styles["my-dashed-class"]} />
```

**React Native CSS modules using [styleName](https://github.com/kristerkari/babel-plugin-react-native-stylename-to-style) property:**

```jsx
<MyElement styleName="myClass my-dashed-class" />
```

## Installation and configuration

### Step 1: Install

```sh
yarn add --dev react-native-stylus-transformer stylus
```

### Step 2: Configure the react native packager

#### For React Native v0.57 or newer

Add this to `rn-cli.config.js` in your project's root (create the file if it does not exist already):

```js
const { getDefaultConfig } = require("metro-config");

module.exports = (async () => {
  const {
    resolver: { sourceExts }
  } = await getDefaultConfig();
  return {
    transformer: {
      babelTransformerPath: require.resolve("react-native-stylus-transformer")
    },
    resolver: {
      sourceExts: [...sourceExts, "styl"]
    }
  };
})();
```

---

#### For React Native v0.56 or older

Add this to `rn-cli.config.js` in your project's root (create the file if it does not exist already):

```js
module.exports = {
  getTransformModulePath() {
    return require.resolve("react-native-stylus-transformer");
  },
  getSourceExts() {
    return ["js", "jsx", "styl"];
  }
};
```

...or if you are using [Expo](https://expo.io/), in `app.json`:

```json
{
  "expo": {
    "packagerOpts": {
      "sourceExts": ["js", "jsx", "styl"],
      "transformer": "node_modules/react-native-stylus-transformer/index.js"
    }
  }
}
```

## Dependencies

This library has the following Node.js modules as dependencies:

- [css-to-react-native-transform](https://github.com/kristerkari/css-to-react-native-transform)
- [semver](https://github.com/npm/node-semver#readme)
