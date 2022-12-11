# node-sandbox


## Setting up typescript

```bash
$ npm i typescript @types/node @tsconfig/node16 ts-node --save-dev
```

Create `tsconfig.json`:
```
{
  "extends": "@tsconfig/node16/tsconfig.json",
  "compilerOptions": {
		"baseUrl": "src"
	},
  "include": ["src"],
  "exclude": ["node_modules"]
}
```

Update your `package.json` `main` and `scripts`:
```json5
  "main": "src/index.ts",
  "scripts": {
    "dev": "NODE_PATH=./src nodemon",
    "start": "NODE_PATH=./dist node dist/index.js",
    "build": "tsc"
  }
```

## Adding linter

```bash
$ npm i eslint --save-dev
$ npm i @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev
```


Create a new file `.eslintrc.js`:
```js
module.exports = {
  parser: "@typescript-eslint/parser",
  parserOptions: {
    ecmaVersion: "latest", // Allows the use of modern ECMAScript features
    sourceType: "module", // Allows for the use of imports
  },
  extends: ["plugin:@typescript-eslint/recommended"], // Uses the linting rules from @typescript-eslint/eslint-plugin
  env: {
    node: true, // Enable Node.js global variables
  },
};
```
