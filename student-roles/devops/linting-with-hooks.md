## Configuring ESLint and Prettier to run on git commit


#### Introduction

In sections 1-3 we set up hooks for eslint and prettier. The result is that when you run `git commit` eslint and prettier check your code. If eslint finds problems, it warns you and prevents the commit. If prettier finds problems, it fixes them and lets the commit continue.

In section 4, we configure vscode (or any editor) to work with eslint and prettier.

The instructions here are for a non-react Node project, but you can find the differences for a React project in section 5


#### 1. Install packages
```
npx install-peerdeps --dev eslint-config-airbnb-base
npm i -D eslint eslint-config-airbnb-base eslint-config-prettier prettier pretty-quick lint-staged husky
```

The first command installs dependencies of the airbnb eslint config. The second installs a whole load of packages - we'll go through them in more detail now. 

#### 2. create config files necessary for eslint and prettier to work
Create ``.eslintrc`` and `.prettierrc` in root directory.

`.eslintrc` should contain (at least)

```
{
    "extends": ["airbnb-base", "prettier"]
}
```

These two extensions are config packages we installed above. `eslint-config-prettier` only _removes_ eslint settings, so it should be combined with another config. `eslint-config-airbnb-base` adds settings back in. It's a relatively strict config file, but it is by far the most popular, so it isn't a bad place for us to start. 

<details>
<summary>Here's a sample .prettierrc, ironically badly formatted</summary>

```json
{
    "printWidth": 80,
    "trailingComma": "all",
	"tabWidth": 4,
	"tabs": true,
    "semi": true,
	"singleQuote": true,
	"quoteProps": "consistent",
	"endOfLine": "lf"
   }

```
</details>

<details>
<summary>Here's a sample .eslintrc</summary>

```jsonld
{
	"extends": ["airbnb-base", "prettier"],
	"rules": {
		"prefer-promise-reject-errors": "off",
		"max-len": ["error", {"code": 80, "ignoreComments": true, "ignoreUrls": true}]
	}
}
    
```

</details>

#### 3. add to your package.json

First lets add two scripts so that we can lint and prettify at will:

```json
	"scripts": {
		"test": "echo \"Error: no test specified\" && exit 1",
		"lint": "eslint .",
		"prettify": "pretty-quick --staged"
	},
```

Now we can run npm run lint and npm run prettify to lint and prettify our code.

Next we'll add two items to the top-level of our package.json, so that eslint and prettier run automatically when we commit. These items are

```json
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.js": [
      "eslint",
      "pretty-quick --staged",
      "git add"
    ]
  },
```

<details>
<summary>A finished package.json might look like this:</summary>

```json
{
  "name": "test-devops",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "husky": {
    "hooks": {
      "pre-commit": "lint-staged"
    }
  },
  "lint-staged": {
    "*.js": [
      "eslint",
      "pretty-quick --staged",
      "git add"
    ]
  },
  "dependencies": {},
  "devDependencies": {
    "eslint": "^6.8.0",
    "eslint-config-airbnb-base": "^14.1.0",
    "eslint-config-prettier": "^6.11.0",
    "eslint-plugin-import": "^2.20.2",
    "husky": "^4.2.5",
    "lint-staged": "^10.2.2",
    "prettier": "^2.0.5",
    "pretty-quick": "^2.0.1"
  },
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}

```
</details>

---
Let's explain the two entries we add to the package.json one by one. 
##### Husky

Husky is a program to help you create and share git hooks. A git hook is something done every time git does a certain thing. In the example above, the git hook occurs on 'pre-commit', i.e. just after you press enter and just before the commit actually happens.

You already have access to git hooks. In any git repo, there is a .git file, which contains a hooks folder. If you remove .sample from the files inside and uncomment their contents, they'll become working git hooks. However, git ignores the .git folder, so you can't share git hooks that you create this way. Husky solves that problem. Because it's a dependency, and you make changes in the package.json, you can share hooks.

##### lint-staged
lint-staged is a program that runs specified commands (the array on the right) only on staged (git-added) files, meaning that you don't have to wait for the computer to lint every file, every time. The \*.js means any file ending with .js, but you could be more or less specific.

One of the programs we call with lint-staged is `pretty-quick`. `pretty-quick` just uses prettier to change files as necessary.


##### It works! (hopefully)
With this setup, when we run git commit, prettier will automatically change formatting errors, and eslint will flag any potential problems for us. If eslint finds serious problems, it will prevent the commit. But before you test this out, make sure your node_modules folder is in your `.gitignore`!

If you ran git commit and committed your node_modules folder you can enter `git rm -r node_modules/ --cached` to remove them from the git repo but not your local folder.

Finally, note that the airbnb config is strict, so it might stop you comitting things you do want to commit.  If you want to _skip_ linter checks and commit, you can use `git commit --no-verify`. This isn't generally recommended, but it's a good thing to have in your arsenal. 


#### 4. Get your text editor on board

There's 3 extensions we'll install. First let's install eslint and prettier. Once you've installed them, you might want to change some of your vscode settings: 
- You should set your default formatter to `esbenp.prettier.vscode`
- maybe set format on save

You can search for all these settings in the settings UI, which you can access by pressing ctrl-shift-p and searching `open settings(UI)`

The last thing we'll install is editorconfig, which reads an `.editorconfig` file and uses it to override vscode's settings. 

In the `.editorconfig` file, you should put at least 

```
root = true
```

But you should in general put other things which fit with your `.prettierrc` and `.eslintrc`. The `.editorconfig` controls what you _enter_ into files, and the `.prettierrc` controls how Prettier _corrects_ what you've entered.

The basic way the `.editorconfig` syntax works is something like CSS: you declare a filetype in square brackets, then on later lines you declare rules for that filetype. If you put a more specific file-selector later, then I presume the later ones override the earlier ones.


<details>
<summary>Here's the file I plan to use</summary>

```
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = false
indent_size = 4
indent_style = tab
max_line_length = off
trim_trailing_whitespace = true

[*.md]
trim_trailing_whitespace = false

```
</details>

#### 5. What about a react app?

A react app is basically the same but some of the packages are different, and some of the stuff you need to write in files is different. 

Install this:

```
npx install-peerdeps --dev eslint-config-airbnb
npm i -D eslint eslint-config-airbnb eslint-config-prettier prettier pretty-quick lint-staged husky
```

The only difference here is the airbnb config we're using.

The config files we write by hand will be different to the ones for non-react projects. In your package.json, delete the field "eslintConfig" (we'll do that in our`.eslintrc`), then add the husky and lint-staged fields from last time, 

```json
	"husky": {
		"hooks": {
			"pre-commit": "lint-staged"
		}
	},
	"lint-staged": {
		"*.js": [
			"eslint",
			"pretty-quick --staged",
			"git add"
		]
	},
```

The `.eslintrc` is different too.
<details>
<summary>Find it here</summary>

```json
{
	"extends": [
		"react-app",
		"airbnb",
		"plugin:jsx-a11y/recommended",
		"prettier",
		"prettier/react"
	],
	"rules": {
		"prefer-promise-reject-errors": "off",
		"max-len": [
			"error",
			{ "code": 80, "ignoreComments": true, "ignoreUrls": true }
		],
		"react/jsx-filename-extension": [1, { "extensions": [".js", ".jsx"] }],
		"react/jsx-one-expression-per-line": [0]
	},
	"plugins": ["jsx-a11y"],
	"env": {
		"es6": true,
		"jest": true,
		"browser": true
	}
}


```
</details>

---

If you also want to add the command `npm run lint` to your `package.json` you'll need to comment out "react-app" in the "extends" field of your `.eslintrc` - I'm not sure which is best.

#### 6. Sources
- [Medium article for React. My main source. Beware typos](https://medium.com/dubizzletechblog/setting-up-prettier-and-eslint-for-js-and-react-apps-bbc779d29062)
- [husky, lint-staged and git hooks](https://www.vojtechruzicka.com/githooks-husky/)
- The npm pages for a lot of these packages
- [Another good article](https://medium.com/@pppped/extend-create-react-app-with-airbnbs-eslint-config-prettier-flow-and-react-testing-library-96627e9a9672)
