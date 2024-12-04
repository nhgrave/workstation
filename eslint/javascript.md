# Eslint configuration for JS

```js
// eslint.config.mjs
import globals from "globals";
import pluginJs from "@eslint/js";
import stylistic from '@stylistic/eslint-plugin';

/** @type {import('eslint').Linter.Config[]} */
export default [
  { files: ["**/*.{js,mjs,cjs}"] },
  {
    ignores: [
      "**/node_modules/**",
      "**/dist/**",
    ],
  },
  {
    languageOptions: {
      globals: {
        ...globals.browser,
      }
    },
  },
  pluginJs.configs.recommended,
  stylistic.configs['recommended-flat'],
  {
    rules: {
      // ...
    }
  }
];
```

## Base Rules from Eslint

```js
{
  'no-empty-function': [
    'error',
    {
      allow: [ 'arrowFunctions' ],
    },
  ],
  'func-style': [ 'error', 'declaration' ],
  'prefer-destructuring': [
    'error',
    {
      array: false,
    },
  ],
  'no-console': [
    (process.env.NODE_ENV === 'production' ? 'error' : 'warn'),
    {
      allow: [ 'warn', 'error' ],
    },
  ],
  'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'warn',
  'no-underscore-dangle': 'off',
  'linebreak-style': 'off',
}
```

## Base Rules from Stylistic

```js
{
  '@stylistic/max-len': [ 'warn', { code: 120, ignoreUrls: true, ignoreRegExpLiterals: true }],
  '@stylistic/indent': [ 'error', 2, { 'SwitchCase': 1 }],
  '@stylistic/keyword-spacing': 'error',
  '@stylistic/object-curly-spacing': [ 'error', 'always' ],
  '@stylistic/comma-spacing': 'error',
  '@stylistic/key-spacing': 'error',
  '@stylistic/comma-dangle': [ 'error', 'always-multiline' ],
  '@stylistic/space-infix-ops': 'error',
  '@stylistic/space-before-blocks': 'error',
  '@stylistic/semi': [ 'error', 'always' ],
  '@stylistic/arrow-spacing': [ 'error', { before: true, after: true }],
  '@stylistic/array-bracket-spacing': [ 'error', 'always', { objectsInArrays: false }],
  '@stylistic/quotes': [ 'error', 'single' ],
  '@stylistic/lines-between-class-members': [ 'error', 'always' ],
  '@stylistic/brace-style': [ 'error', '1tbs' ],
}
```
