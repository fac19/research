# Monorepo Deployment

## Root Folder

### `package.json`
It's helpful to have scripts that run your front and back end servers from the root folder so you don't have to move into them constantly.

For example:
```json
"scripts": {
  "app": "cd front-end-folder && npm start",
  "api": "cd back-end-folder && npm start",
  "app-test": "cd front-end-folder && npm test",
  "api-test": "cd back-end-folder && npm test"
}
```

## Pre-commit Hooks

### Prettier
Keep `.prettierrc` config file in the root folder.

### ESLint
Keep `.eslintrc.js` config file in the back-end folder.

### Husky
You can configure pre-commit hooks in Husky to run prettier on the whole project repo (just on the staged files using pretty-quick npm package), and linting on just the back end directory.

```json
"scripts": {
  "prettier": "./node_modules/.bin/prettier . --write",
  "backendlint": "./back-end-folder/node_modules/.bin/eslint back-end-folder --fix"
}
"devDependencies": {
  "husky": "^4.2.5",
  "prettier": "^2.0.5",
  "pretty-quick": "^2.0.1"
},
"husky": {
  "hooks": {
    "pre-commit": "pretty-quick --staged && npm run backendlint"
  }
}
```


## Deploying React app on Netlify
- The first deploy when you connect the GitHub repo will fail because you can't configure the full Deploy settings on the initial set-up stage  
- In Settings > Build Settings:  
**Base directory:** front-end-folder  
**Build command:** npm run build  
**Publish directory: front-end-folder/** build

## Deploying REST API on Heroku
- Make sure you have a `package.json` in the root folder
- Heroku builds default to `npm start` from the root, to configure this you need to add a `Procfile` to your root folder to include the custom build script
```
web: cd back-end-folder && npm i && npm start
```

## Running CI with Travis
- Add a `.travis.yml` file in the root folder
- Pray (I still can't get this to work help!)
