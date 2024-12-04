# Plugin for React

```bash
npm install -D eslint-plugin-react
```

changes files to support jsx

```js
/** @type {import('eslint').Linter.Config[]} */
export default [
  { files: [ '**/*.{js,mjs,cjs,jsx}' ] },
  // ...
  {
    languageOptions: {
      parserOptions: {
        ecmaFeatures: {
          jsx: true,
        },
      },
    },
  },
];
```
