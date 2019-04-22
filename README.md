Photo Storage Api

A simple example to use AdonisJS to proveider resources.

Frameworks:

AdoniJS

Node Dependencies:

- Packages:
  - Adonis
- Development Dependencies:
  - Typescript
  - Sucrase
  - Nodemon
  - Eslint
  - Prettier

Configuring the behavior development

In the next lines we will see how configure a standard development behavior
development using adonisJS + typescript + sucrase + nodemon. this configuration ins very important when we are to working in a collaboratives projects, and facilitate the process of inspection and fetch of problems.

Obs:. The install commands bellow could be executed in the terminal( for unix systems ). Please install `yarn` package manager:

Mac OS: `brew install yarn`
Linux: `apt-get install yarn`

But, if you to want continue with `npm` control package, when you see `yarn add -D {some package to install}` in this document subscribe to `npm install --save-dev {package to install}`, to show more npm commands please access this link:
https://docs.npmjs.com/

Typescript: Provide types structure to check code type during development

1. Install: `yarn add -D typescript --save-dev`
2. Change yout serverfile, server.js -> server.ts

Sucrase: Convert typescript to java script very fast.

1. Install: `yarn add -D sucrase --save-dev`
2. Configuring:
   In package.json change the build script

```
{... "scripts": {
    // Execute the build command in a specific path and transforms
    // ts files in js files and imports/export to
    // require/module.export (CommonJs)
    "build": "sucrase ./app -d public/js
    --transforms typescript,imports",
    }
}
```

Execute: `yarn build` or `npm build` (when use npm)

Nodemon: Listen for all the changes in js/ts files, configured in "nodemon.json" file

1. Install: `yarn add -D nodemon`
   configuring: 1) Create a nodemon.json file in root path project

2. Configure nodemon file

```
{
    //Here we need to put the path that will go to observer the changes
    "watch":["app"],
    //The extensions set that will be observable
    "ext":"ts",
    //When a ".ts" file changed execute this command below
    "execMap":{
    "ts": "sucrase ./app -d public/js"
    }
}
```

3. Change the node command {... `node server.ts` ...} in package.json to
   `nodemon server.ts`

Eslint: Standardization os source code, this plugn is very usefull when we are developing in a team or open source colaboration projects.

Install: `yarn add -D eslint @typescript-eslint/parser @typescript-eslint/eslint-plugin --save-dev`

Configuring: 1) Execute the command: `yarn eslint --init` or `npm eslint --init`

2. Choice the 3rd option "To Check syntax, find problems, and enfor..." and press enter
3. Select "JavaScript modules `(import/export)`" and press "enter"
4. Choice "None of these" and press enter
5. Select "Node" option, you need to use "space" in the keyboard to select "Node option". Please unselect the "Browser" option if selected.
6. Choice the use a "Popular style guide", and press enter
7. Select "Standard option", and press enter.
8. Choice configuration file format, please select "java Script" option, and press enter.

To wait the library installs
Obs:. If you want to use only yarn to manage of the libs, you need to remove the "package-lock.json" and run the command: `yarn` in the project folder and the yarn will go to capture the new dependencies installed with `npm`.

Editing .eslint file:

Add the codes bellow in your .eslint file.

```
module.exports = {
    + parser: '@typescript-eslint/parser',
    'env': {
    'es6': true,
    'node': true
    },
    + plugins: ['@typescript-eslint'],
    'extends': [
    +'plugin:@typescript-eslint/recommended',
    +'prettier/@typescript-eslint',
    'standard'
    ],
    'globals': {
    'Atomics': 'readonly',
    'SharedArrayBuffer': 'readonly'
    },
    'parserOptions': {
    'ecmaVersion': 2018,
    'sourceType': 'module'
    },
    'rules': {

    },
    "globals": { "use": true}
}
```

Open the visual Studio Code Settings press "command + ," on macos or Open via Menu in "Code -> Preferencies -> Settings" click in "{}" nutton in the right up side, and add these specifications:

```
{
  ...
  "eslint.autoFixOnSave": true,
  "eslint.validate": [
  "javascript",
  "javascriptreact",
  {"language": "typescript", "autoFix": true },
  {"language": "typescriptreact", "autoFix": true }
  ],
  ...
  }
```

Still in settings file and if you installed prettier plugin in vscode and the option "editor.formatOnSave": true," is "true", please add these two more specification and you don't will go to have conflicts between prettier formatOnSave configured:

```
{
...
  "[typescript]":{
  "editor.formatOnSave": false,
  },
  "[typescriptreact]":{
  "editor.formatOnSave": false,
  },
  ...
  }
```

Close the VS Code Application and re-open in your project.

If you find some bugs about the development behavior configuration please create up an issue and share with us your problem.

Things to do:

- Review the english sentences;
- Put Adonis Types Set for typescript and configure;
- Create a Docker tutorial and to include in README.md;
  And more things that you considered cool...
