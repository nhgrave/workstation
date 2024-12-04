# Plugin for TypeScript

Install the following lib `typescript-eslint`

```bash
npm install -D typescript-eslint
```

## Base Rules from TypeScript

```js
{
  '@typescript-eslint/no-explicit-any': 'warn',
  '@typescript-eslint/explicit-function-return-type': 'off',
  '@typescript-eslint/typedef': [
    'error',
    {
      arrowParameter: true,
      memberVariableDeclaration: true,
      parameter: true,
      propertyDeclaration: true
    }
  ],
}
```
