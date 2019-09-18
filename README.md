# css-vars-media

> Easily define custom properties and their variants

[![npm version](https://badge.fury.io/js/css-vars-media.svg)](https://npmjs.org/package/css-vars-media "View this project on npm")
[![MIT license](https://img.shields.io/badge/License-MIT-blue.svg)](https://github.com/VeronQ/css-vars-media/blob/master/LICENSE)

![Demo CLI](../assets/screenshot.png?raw=true)

## Installation

```sh
$ npm install --save-dev css-vars-media
```

## Usage

#### 1. Import `css-vars-media`.
```scss
@import '~css-vars-media/lib/css-vars-media.scss';
```

#### 2. Define your media queries rules.
```scss
$medias: (
  sm-up: 'screen and (min-width: 576px)',
  md-up: 'screen and (min-width: 768px)',
);
```

#### 3. Define your custom properties and their variants.

```scss
$theme: (
  --container-gutter: (
    '20px',
    (
      sm-up: '40px',
      md-up: '60px',
    )
  ),
  --map-height: (
    '320px',
    (
      sm-up: '400px',
      md-up: '560px',
    )
  ),
);
```


##### 4. Finally, use `css-vars-media` mixin to generate all custom properties.

```scss
@include css-vars-media($theme, $medias);
```

## API

### $medias

List of all medias queries used for `@css-vars-media` *$theme* parameter.

Type: `map`  

  - key: `string` [unquoted] - (Media query alias)
  - value: `string` [quoted] - (Media query rule)
  
**Example:**

```scss
$medias: (
  portrait: '(orientation: portrait)',
  landscape: '(orientation: landscape)',
);
```

### $theme

List of all custom properties and their variants.

Type: `map`

  - key: `string` [unquoted] - (Custom property)
  - value: `list` [2 values]
    - 1st value: `string` [quoted] - (Default value)
    - 2nd value: `map`
      - key: `string` [unquoted] - (Media query alias)
      - value: `string` [quoted] - (Variant value)

**Example:**

```scss
$theme: (
  --my-custom-variable: (
    'blue',
    (
      sm-up: 'red',
      md-up: 'green'
    )
  ),
);
```


### @css-vars-media(theme, medias)

Mixin used to generate all custom properties.

Type: `mixin`

Refer to `$theme` and `$medias`.

## Support

See current [support for Custom Properties](https://caniuse.com/#feat=css-variables).

> **92.85%** support as of September 2019.

## License

[MIT](https://github.com/VeronQ/css-vars-media/blob/master/LICENSE)
