---
title: 记录自用eslint架构配置
date: 2023-07-28 23:02:44
tags: ["eslint"]
---
vue适用eslint方案，验证规则很松，主要适用默认推荐和prettier

## .eslintrc.js
``` javascript
module.exports = {
  root: true,
  env: {
    node: true
  },
  extends: ['plugin:vue/essential', 'eslint:recommended', '@vue/prettier'],
  parserOptions: {
    parser: 'babel-eslint'
  },
  rules: {
    'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
    eqeqeq: 2,
    'no-const-assign': 2,
    'no-unused-vars': 0,
    'no-eq-null': 2
  }
};
```
## prettier.config.js
``` javascript
module.exports = {
  singleQuote: true,
  bracketSpacing: true,
  semi: true,
  tabWidth: 2,
  printWidth: 160,
  trailingComma: 'none'
};

```