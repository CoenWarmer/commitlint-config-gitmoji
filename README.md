> Lint your gitmoji commits

# commitlint-config-gitmoji

[English](./README.md) | [中文](./README_zh-cn.md)

Shareable `commitlint` config enforcing gitmoji.
Use with [@commitlint](https://github.com/marionebl/commitlint) .

## Demo

TODO

## Getting started

1 - Install dependencies

```sh
# use npm
npm i -D commitlint-config-gitmoji @commitlint/core

# use yarn
yarn add -D commitlint-config-gitmoji @commitlint/core
```

2 - Add commitlint config for Gitmoji

```sh
echo "module.exports = {extends: ['./node_modules/commitlint-config-gitmoji']};" > commitlint.config.js
```

## Rules

### Problems

The following rules are considered problems for `gitmoji commit` and will yield a non-zero exit code when not met.

Consult [docs/rules](http://marionebl.github.io/commitlint/#/reference-rules) for a list of available rules.

#### type-enum

- **condition**: `type` is found in value
- **rule**: `always`
- **value**

```js
[
  ':art:',
  ':zap:',
  ':fire:',
  ':bug:',
  ':ambulance:',
  ':sparkles:',
  ':pencil:',
  ':rocket:',
  ':lipstick:',
  ':white_check_mark:',
  ':lock:',
  ':bookmark:',
  ':rotating_light:',
  ':construction:',
  ':green_heart:',
  ':arrow_down:',
  ':arrow_up:',
  ':pushpin:',
  ':construction_worker:',
  ':chart_with_upwards_trend:',
  ':recycle:',
  ':heavy_plus_sign:',
  ':heavy_minus_sign:',
  ':wrench:',
  ':hammer:',
  ':globe_with_meridians:',
  ':pencil2:',
  ':poop:',
  ':rewind:',
  ':twisted_rightwards_arrows:',
  ':package:',
  ':alien:',
  ':truck:',
  ':page_facing_up:',
  ':boom:',
  ':bento:',
  ':wheelchair:',
  ':bulb:',
  ':beers:',
  ':speech_balloon:',
  ':card_file_box:',
  ':loud_sound:',
  ':mute:',
  ':busts_in_silhouette:',
  ':children_crossing:',
  ':building_construction:',
  ':iphone:',
  ':clown_face:',
  ':egg:',
  ':see_no_evil:',
  ':camera_flash:',
  ':alembic:',
  ':mag:',
  ':label:',
  ':seedling:',
  ':triangular_flag_on_post:',
  ':goal_net:',
  ':dizzy:',
  ':wastebasket:',
],
```

```sh
echo ":abc: some message" # fails
echo ":bento: some message" # passes
```

#### type-case

- **description**: `type` is in case `value`
- **rule**: `always`
- **value**
  ```js
  "lowerCase";
  ```

```sh
echo ":ART: Format some code" # fails
echo ":art: Format some code" # passes
```

#### type-empty

- **condition**: `type` is empty
- **rule**: `never`

```sh
echo ": some message" # fails
echo ":fire: Delete some file" # passes
```

#### scope-case

- **condition**: `scope` is in case `value`
- **rule**: `always`

```js
"lowerCase";
```

```sh
echo ":art:(SCOPE) some message" # fails
echo ":art:(scope) some message" # passes
```

#### subject-case

- **condition**: `subject` must begin with `['sentence-case', 'start-case', 'pascal-case', 'upper-case']`
- **rule**: `always`

```sh
echo ":art:(scope) some Message" # Fails
echo ":art:(scope) Some message" # pass
```

#### subject-empty

- **condition**: `subject` is empty
- **rule**: `never`

```sh
echo ":art: " # fails
echo ":art: some message" # passes
```

#### subject-full-stop

- **condition**: `subject` ends with `value`
- **rule**: `never`
- **value**

```js
".";
```

```sh
echo ":art: some message." # fails
echo ":art: some message" # passes
```

#### header-max-length

- **condition**: `header` has `value` or less characters
- **rule**: `always`
- **value**

```js
72;
```

```sh
echo ":art: some message that is way too long and breaks the line max-length by several characters" # fails
echo ":art: some message" # passes
```

## parserPreset

```js
parserPreset: {
    parserOpts: {
      headerPattern: /^(:\w*:)(?:\((.*?)\))?\s((?:.*(?=\())|.*)(?:\(#(\d*)\))?/,
      headerCorrespondence: ['type', 'scope', 'subject', 'ticket'],
    }
}
```

## Gitmoji Reference Sheet

Refer to the [Gitmoji Reference](https://gitmoji.carloscuesta.me/) for descriptions of gitmojis.
