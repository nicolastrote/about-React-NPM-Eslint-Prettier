# about-React-NPM-Eslint-Prettier 
About npm, React, Eslint and Prettier installation for React developers

## Motivation 

Create-react-app in npx@^7.4.0 used eslint@6.6.0 which wasn't working with react. React was expected the version 7.2.0.
Here I am testing the last version of create-react-app and display a proper path to update your dev environment.

## Table of contents

- [about-React-NPM-Eslint-Prettier](#about-react-npm-eslint-prettier)
  - [Motivation](#motivation)
  - [Table of contents](#table-of-contents)
  - [NodeJS Install & Upgrade](#nodejs-install--upgrade)
  - [Clean Up](#clean-up)
  - [NPM Upgrade](#npm-upgrade)
  - [NPX Upgrade](#npx-upgrade)
  - [Create-React-App](#create-react-app)
  - [Eslint](#eslint)
  - [Prettier](#prettier)
  - [Eslint Config File](#eslint-config-file)
  - [Eslint Ignore File](#eslint-ignore-file)
  - [Eslint & Prettier Scripts](#eslint--prettier-scripts)
  - [VSCode configuration](#vscode-configuration)
  - [Test](#test)
  - [Resolving The Eslint Errors](#resolving-the-eslint-errors)
  - [VSCode Does Not Display Eslint/Prettier Errors](#vscode-does-not-display-eslintprettier-errors)
  - [HUSKY](#husky)
  - [How to Debug the Code](#how-to-debug-the-code)
  - [SCSS](#scss)
  
## NodeJS Install & Upgrade

For using react-create-app, latest LTS version of NodeJS is recommended by this project.

* website: choose LTS from [NodeJS](https://nodejs.org)
* nvm : `nvm install node --reinstall-packages-from=node`
* Brew : `brew upgrade && brew upgrade node`
* Chocolatey : `choco install nodejs-lts`

## Clean Up

Some packets could stay in your global and need to be delete for no conflicts.
List all global packets : 

```shell
npm list -g --depth 0

// My minimum of packages is :
C:\Users\x\AppData\Roaming\npm
├── expo-cli@4.1.6
├── nodemon@2.0.7
├── npm-check@5.9.2
├── npm@7.5.2
├── npx@10.2.2
├── react-devtools@4.10.1
├── react-native-cli@2.0.1
├── yarn-check@0.0.3
└── yarn@1.22.10
```shell
and remove unwanted with:

```shell
npm remove -g [package]
```

## NPM Upgrade

Upgrade of npm
```shell
npm install -g npm@latest
```
Validate that all global packages are update:

```shell
npm i -g npm-check && npm-check -g -y
```
` npm --version` reply `7.5.2`

## NPX Upgrade

Upgrade of npx
```shell
npm install -g npx --force
```

` npx --version` reply `7.5.2` (same as npm, we're good!)

## Create-React-App

Now we can testing if create-react-app is working properly with typescript, eslint and prettier

```shell
npx create-react-app web-app --template typescript
```

- first test: 
```shell
cd web-app && yarn start
```

## Eslint
Eslint installation:
```shell
yarn add -D @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-config-airbnb-typescript eslint-plugin-jest
```

Install of Airbnb config
```shell
npx install-peerdeps --dev eslint-config-airbnb
```

## Prettier
Prettier installation:
```shell
yarn add -D prettier eslint-config-prettier eslint-plugin-prettier
```

## Eslint Config File
Create .eslintrc.js file :
```JS
module.exports = {
  root: true,
  extends: [
    'airbnb-typescript',
    'airbnb/hooks',
    'plugin:@typescript-eslint/recommended',
    'plugin:jest/recommended',
    'plugin:prettier/recommended',
    'prettier',
    'prettier/@typescript-eslint',
    'prettier/react',
    "eslint:recommended",
    "plugin:@typescript-eslint/eslint-recommended",
  ],
  plugins: ['react', '@typescript-eslint', 'jest'],
  env: {
    browser: true,
    es6: true,
    jest: true,
  },
  globals: {
    Atomics: 'readonly',
    SharedArrayBuffer: 'readonly',
  },
  parser: '@typescript-eslint/parser',
  parserOptions: {
    ecmaFeatures: {
      jsx: true,
    },
    ecmaVersion: 2018,
    sourceType: 'module',
    project: './tsconfig.json',
  },
  rules: {
    'no-console': 'off',
    'no-explicit-any': 'off',
    'prettier/prettier': [
      'error',
      {
        endOfLine: 'auto',
      },
    ],
    'no-multiple-empty-lines': ['warn', { max: 1, maxEOF: 1 }],
    '@typescript-eslint/explicit-function-return-type': 'off',
    '@typescript-eslint/explicit-member-accessibility': 'off',
    '@typescript-eslint/interface-name-prefix': 'off',
    'import/prefer-default-export': 'off',
    'newline-before-return': ['warn'],
    indent: ['error', 2, { SwitchCase: 1 }],
    'no-multi-spaces': ['warn'],
    'max-len': [
      'warn',
      {
        code: 100,
        ignoreComments: true,
        ignoreTrailingComments: true,
        ignoreUrls: true,
        ignoreTemplateLiterals: true,
        ignoreRegExpLiterals: true,
      },
    ],
    'prefer-promise-reject-errors': ['off'],
    'no-return-assign': ['warn'],
    'no-dupe-keys': ['warn'],
    'no-useless-escape': ['warn'],
    yoda: ['warn'],
    'no-underscore-dangle': ['off'],
    'no-param-reassign': ['off'],
    'no-var': ['warn'],
    'no-unused-vars': ['warn'],
    'prefer-const': ['warn'],
    'no-plusplus': ['warn', { allowForLoopAfterthoughts: true }],
    'no-shadow': [
      2,
      {
        hoist: 'all',
        allow: ['resolve', 'reject', 'done', 'next', 'err', 'error'],
      },
    ],
    'no-buffer-constructor': ['warn'],
    'prefer-destructuring': ['warn'],
    'spaced-comment': ['warn'],
    strict: ['warn'],
    'import/newline-after-import': ['warn'],
    'import/order': [
      'warn',
      {
        groups: ['external', 'internal', 'parent', 'sibling', 'index', 'builtin'],
        'newlines-between': 'always',
      },
    ],
    'no-else-return': ['warn'],
    'consistent-return': ['warn'],
    'lines-around-directive': ['warn'],
    'prefer-template': ['warn'],
    'one-var': ['warn'],
    'no-useless-rename': ['warn'],
    'array-callback-return': ['warn'],
    'new-cap': ['warn'],
    'vars-on-top': ['warn'],
    'no-lonely-if': ['warn'],
    'no-useless-concat': ['warn'],
    'no-unused-expressions': ['warn'],
    'no-unneeded-ternary': ['warn'],
    radix: 0,
    'no-nested-ternary': ['warn'],
    camelcase: ['warn'],
    'import/no-extraneous-dependencies': ['off'],
    'import/no-dynamic-require': ['off'],
    'no-new-require': ['warn'],
    'operator-assignment': ['warn'],
    'global-require': ['warn'],
    'no-multi-assign': ['warn'],
    'no-restricted-syntax': ['warn'],
    'guard-for-in': ['warn'],
    'dot-notation': ['warn'],
    'no-unreachable': ['warn'],
    'newline-per-chained-call': ['warn', { ignoreChainWithDepth: 2 }],
    quotes: ['warn', 'single'],
    'padding-line-between-statements': [
      'warn',
      { blankLine: 'always', prev: '*', next: ['return', 'block-like'] },
      {
        blankLine: 'always',
        prev: 'block-like',
        next: '*',
      },
    ],
    'jsx-a11y/href-no-hash': 'off',
    'jsx-a11y/anchor-is-valid': [
      'warn',
      {
        aspects: ['invalidHref'],
      },
    ],
    'react/display-name': 1,
    'react/no-array-index-key': 0,
    'react/react-in-jsx-scope': 0,
    'react/prefer-stateless-function': 0,
    'react/prop-types': ['off'],
    'react/forbid-prop-types': 0,
    'react/no-unescaped-entities': 0,
    'jsx-a11y/accessible-emoji': 0,
    'react/require-default-props': 0,
    'react/jsx-filename-extension': [
      1,
      {
        extensions: ['.js', '.jsx', '.tsx'],
      },
    ],
    'react-hooks/rules-of-hooks': 'warn',
    'react-hooks/exhaustive-deps': 'off',
    'react/jsx-curly-spacing': 'warn',
    'object-curly-spacing': ['error', 'always'],
  },
};
```
nb: for more info read [here](https://github.com/typescript-eslint/typescript-eslint/blob/master/docs/getting-started/linting/README.md)

## Eslint Ignore File
Create .eslintignore file :
```s 
# don't ever lint node_modules
node_modules
# don't lint build output (make sure it's set to your correct build folder name)
dist
# don't lint nyc coverage output
coverage
# don't lint .eslintrc.js
.eslintrc.js
```

## Eslint & Prettier Scripts
Add scripts to your package.json file:
```JSON
"scripts": {
  "format": "prettier --write src/**/*.ts{,x}",
  "lint": "tsc --noEmit && eslint src/**/*.ts{,x}"
}
```

## VSCode configuration
In your json settings file:
```JSON
{
  "files.associations": {
    "*.jsx": "javascriptreact"
  },
  "editor.insertSpaces": true,
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true, /* This allow fix for eslint + prettier */
    "source.fixAll": true,
    "source.organizeImports": false /* Can be turned on */
  },
  "json.format.enable": true,
  "files.autoSave": "onFocusChange",
  "editor.tabSize": 2,
  "editor.detectIndentation": false,
  "typescript.updateImportsOnFileMove.enabled": "always",
  "javascript.updateImportsOnFileMove.enabled": "always",
  "cSpell.userWords": [
    "browserslist",
    "choco",
    "linebreak",
    "peerdeps"
  ],
}
```

## Test
Launch the web app
```shell
λ yarn start
yarn run v1.22.10
$ react-scripts start

There might be a problem with the project dependency tree.
It is likely not a bug in Create React App, but something you need to fix locally.

The react-scripts package provided by Create React App requires a dependency:

  "eslint": "^7.11.0"

Don't try to install it manually: your package manager does it automatically.
However, a different version of eslint was detected higher up in the tree:

  C:\Users\x\Workspace\boilerplate-react-typescript-hooks-context-app-2\node_modules\eslint (version: 7.2.0)
```

## Resolving The Eslint Errors
The error pop, so we can use yarn-check to solve conflicts:
```shell
yarn add yarn-check -g && yarn-check -u
...
[yarn-check] Update complete!
[yarn-check] eslint@7.19.0, eslint-plugin-react@7.22.0, @types/node@14.14.25, eslint-plugin-react-hooks@4.2.0
[yarn-check] You should re-run your tests to make sure everything works with the updates.
```

Error is gone ;-)

## VSCode Does Not Display Eslint/Prettier Errors
> NOTE: if eslint doesn't display errors in VSCode, try this to force the display: `yarn eslint . --ext .js,.jsx,.ts,.tsx`

## HUSKY

Husky can prevent bad git commit, git push and more 🐶 woof!
> NOTE: to get ride of warning: LF will be replaced by CRLF in

```shell
yarn add -D husky lint-staged
```

- Add in your package.json some hooks and scripts : 
```JSON
"lint-staged": {
    "*.{js,jsx,ts,tsx}": [
      "yarn lint:fix",
      "yarn format"
    ]
  },
"husky": {
  "hooks": {
    "pre-commit": "lint-staged",
    "pre-push": "lint-staged && yarn run test-ci"
  }
},
```

## How to Debug the Code

- Install the plugin: Debugger for Chrome msjsdiag.debugger-for-chrome
- In VSCode clic on the icon for debugging
- Click on the link "create a launch.json file"
- Select "Chome (Preview)"

It create a launch.json file under .vscode to parameter debugging:
```JSON
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "pwa-chrome",
            "request": "launch",
            "name": "Launch Chrome against localhost",
            "url": "http://localhost:3000/",
            "webRoot": "${workspaceFolder}"
        }
    ]
}
```
- change url for http://localhost:3000/
- go on the App.tsx file, for example, put a break point and launch debug with F5

## SCSS

- `yarn add sass classnames`

> ⚠ NOTE : `yarn add node-sass` will lead to bad issues at time: [https://github.com/webpack-contrib/sass-loader/issues/898](issue)

- Rename src/App.css to src/App.scss and update src/App.tsx to import src/App.scss
- Rename src/index.css to src/index.scss and update src/Dashboard.tsx to import src/index.scss

