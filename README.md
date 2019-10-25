# Create React APP Manually
This tutorial show how to create React app without any scaffold like "create-react-app".

# Step 0
First, we need install `NodeJs` and dependency management tool, `Yarn` is recommend in this tutorial.

Install NodeJs with your local system package installer, for example

```bash
apt install nodejs
```

Then install Yarn globally.

```bash
npm install yarn -g
```

# Step 1
Use Yarn to generate `package.json` for us.

```bash
yarn init
```

Type all the info yarn wants, or just press ENTER all the way.

# Step 2
Since React use `jsx`, we need compile the code to normal js that can be run in browser.

This tutorial recommend [`Parcel`](https://parceljs.org/), a zero configuration bundler.

```bash
yarn add parcel-bundler --dev
```

# Step 3
Add React dependencies to project

```bash
yarn add react react-dom react-router react-router-dom
```

# Step 4
Now, create some directories and files.

```bash
mkdir public
touch public/index.html
mkdir src
touch src/index.jsx
```

Most simplified `index.html` example:

```html
<!doctype html>
<html lang="en">
<head>
    <title>SiteName</title>
</head>
<body>
<div class="root" id="root"></div>
<script src="../src/index.jsx"></script>
</body>
</html>
```

Most simplified `index.jsx` example:

```jsx harmony
import React from "react";
import ReactDOM from "react-dom";

ReactDOM.render(<p>HelloWorld!</p>, document.getElementById("root"));
```

# Step 5
Add scripts and run the project.

`package.json` example:

```json
{
  "name": "create-react-app-manually",
  "version": "1.0.0",
  "main": "index.js",
  "license": "MIT",
  "devDependencies": {
    "parcel-bundler": "^1.12.4"
  },
  "dependencies": {
    "react": "^16.11.0",
    "react-dom": "^16.11.0",
    "react-router": "^5.1.2",
    "react-router-dom": "^5.1.2"
  },
  "scripts": {
    "start": "parcel public/index.html",
    "build": "parcel build public/index.html"
  }
}
```

Command:

```bash
yarn start
```

Click the link printed in console(http://localhost:1234/) to preview your project.

After modified files in project, just press `Ctrl-S` to save all files, parcel will hot reload them.

# Additional
If more babel plugins needed, create a file in project root named `.babelrc`, and write plugins in it, for example:

```json
{
  "plugins": [
    "@babel/plugin-proposal-do-expressions",
    "@babel/plugin-proposal-nullish-coalescing-operator",
    "@babel/plugin-proposal-optional-chaining",
    "@babel/plugin-proposal-partial-application",
    "@babel/plugin-proposal-class-properties",
    "@babel/plugin-transform-flow-strip-types",
    "@babel/plugin-transform-react-constant-elements"
  ]
}
```

parcel will automatic detect this file and install them.

Simple is the best.
