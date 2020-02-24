# Basic ESLint and Prettier Config for JavaScript, TypeScript and React 👨‍💻

## What this setup provides

* Lints JavaScript/TypeScript based on the current standards
* Fixes formatting issues with Prettier
* Lints + Fixes React and React Hooks based on the eslint config of airbnb with some minor changes to it based on my preferences
* [See the applied rules](https://github.com/d4ny0/eslint-config-d4ny0/eslintrc.js)

## Getting up and running 🏃‍♂️

I use this setup globally to have linting for random JavaScript Files but you can also install this on a per project basis.

## Local / per Project Install 📂

1. If you have a `package.json` in your project you can skip this step. Otherwise create a `package.json` with `npm init`.
2. Install this configuration by running
```
npx install-peerdeps eslint-config-d4ny0
```
3. You can see all the installed packages in the `devDependencies` section of your `package.json`
4. In the root directory of your project (That's where your `package.json` lives aswell). Create a `.eslintrc.js` or `.eslintrc` file and fill it with:

```json
{
  "extends": [
    "d4ny0"
  ]
}
```
*To reduce file clutter in your project you alternatively can put this object in your `package.json` under the property `"eslintConfig":`.*

## Global Install 🌍

1. Install the configuration and all dependencies globally
```
npx install-peerdeps --global eslint-config-d4ny0
```
2. Create a global `.eslintrc` or `.eslintrc.js` file. ESLint will look in your home directory
* `~/.eslintrc` or `~/.eslintrc.js` on a mac
* `C:\Users\{username}/.eslintrc` or `C:\Users\{username}/.eslintrc.js` on windows

The Content of if this file should look like this

```json
{
  "extends": [
    "d4ny0"
  ]
}
```

## Run your linter from the Command Line 💻

After the setup step you can add the following code to your `"scripts"` section of your `package.json` to run the linter from the commandline.
* run `npm run lint` to lint your errors
* run `npm run lint:fix` to lint and automatically fix all fixable issues.

```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix"
},
```

## Let your Editor take care of linting/fixing (settings for VS Code)

1. Install the [ESLint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
2. Setup Vs Code settings via `Code` → `Preferences` → `Settings` (or hit `cmd + ,` on a mac). To get to the `json` view click the `Open Settings (JSON)` icon in the top right corner.

```js
"editor.formatOnSave": true //runs auto formatting for all files
//turns of auto formatting for JS, JSX, TS and TSX because eslint takes care of this
"[javascript, typescript]": {
  "editor.formatOnSave": false
},
//tells the eslint plugin to run when we save
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
},
"eslint.run": "onSave", //runs eslint when you save a file
"eslint.validate": [ //sets filetypes eslint watches
  "javascript",
  "javascriptreact",
  "typescript",
  "typescriptreact"
],
"eslint.alwaysShowStatus": true, //shows the eslint status in the status bar

/* OPTIONAL SETTING if you have the prettier VS Code Extension installed
 * This code tells the exentsion that we already take care of formatting these filetypes
 */
"prettier.disableLanguages": [
  "javascript",
  "javascriptreact",
  "typescript",
  "typescriptreact"
]
```
## Extend/Overwrite this config

You can overwrite both `eslint` and `prettier` settings in your own `.eslintrc` or `eslintrc.js` file.
* [ESLint rules](https://eslint.org/docs/rules/) are written under `"rules"`
* [Prettier Settings]() are inside the `"rules"` under `"prettier/prettier"`. Prettier rules overwrite everything previous defined so you have to write settings that you would like to keep aswell

### Extension Example:
```js
{
  "extends": [
    "d4ny0"
  ],
  "rules": {
    "react/prefer-stateless-function": 2,
    "prettier/prettier": [
      "error",
      {
        "bracketSpacing": true,
        "printWidth": 120,
        "singleQuote": true,
        "useTabs": true, //don't @ me for this 👾
        "tabWidth": 4,
        "trailingComma": "es5"
      }
    ]
  }
}
```


## 💩💩💩 When it's not working 💩💩💩

There's the possibility that global modules fail on installation. This will remove them from your system to start out fresh.

```
npm remove --global eslint-config-d4ny0 eslint eslint-config-airbnb eslint-config-prettier eslint-plugin-html eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier typescript @typescript-eslint/parser @typescript-eslint/eslint-plugin
```
*For a local installation omit the `--global` flag. After that follow the setup guide again.*

---
## **🙌 Feel free to contribute to this setup 🙌**
