# Plugin for Vue

```bash
npm install -D eslint-plugin-vue
```

if you use typescript add the following plugin

```bash
npm install -D @vue/eslint-config-typescript
```

```js
// eslint.config.js
import pluginVue from "eslint-plugin-vue";

export default [
  { files: ["**/*.{js,mjs,cjs,vue}"] },
  // ...
  ...pluginVue.configs['flat/recommended'],
  // ...
];
```

## Base Rules from Vue

```js
{
  'vue/no-v-html': 'warn',
  'vue/no-v-text-v-html-on-component': 'warn',
  'vue/html-indent': [
    'error',
    2,
    { attribute: 1, baseIndent: 1, closeBracket: 0, alignAttributesVertically: true, ignores: [] },
  ],
  'vue/script-indent': [ 'error', 2, { baseIndent: 0, switchCase: 1 }],
  'vue/singleline-html-element-content-newline': 'off',
  'vue/multiline-html-element-content-newline': 'off',
  'vue/html-closing-bracket-newline': [ 'error', { singleline: 'never', multiline: 'always' }],
  'vue/component-definition-name-casing': [ 'error', 'PascalCase' ],
  'vue/no-unused-components': 'error',
  'vue/no-unused-vars': 'error',
  'vue/padding-line-between-blocks': 'error',
  'vue/max-attributes-per-line': [ 'error', { singleline: { max: 3 }, multiline: { max: 1 } }],
  'vue/first-attribute-linebreak': [ 'error', { singleline: 'ignore', multiline: 'below' }],
  'vue/block-lang': [ 'warn', { i18n: { lang: 'json' } }],
  'vue/enforce-style-attribute': [ 'error', { allow: [ 'scoped' ] }],
}
```
