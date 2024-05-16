## v2.0.0

- Breaking: drop support for `react-native` versions older than 0.59
- Removed: `semver` dependency.
- Added: support for `Expo SDK` v50.

## v1.2.0

- Added: `renderToCSS` method. It can be used together with the PostCSS transformer to add support for CSS variables.

## v1.1.4

- Updated: `semver` dependency to v5.6.0.
- Updated: `css-to-react-native-transform` dependency to v1.8.1.

## v1.1.3

- Fixed: Compatibility with react-native v0.59

## v1.1.2

- Updated: `css-to-react-native-transform` dependency to v1.7.0.

## v1.1.1

- Fixed: Compatibility with react-native v0.56

## v1.1.0

- Updated: `css-to-react-native-transform` dependency to v1.6.0.
- Added: enabled parsing of CSS viewport units (does not work without `babel-plugin-react-native-classname-to-dynamic-style`).

## v1.0.1

- Fixed: pass `filename` to `stylus.render` to allow `@import` and `@require` to work properly.

## v1.0.0

- Initial release
