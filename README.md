# react-publish-guide
This is a simple guide for publishing react components to npm.

# Why
I've recently started publishing small, reusable React components to npm and after trying to do this with the tools that I'm used to, I've found that the process was far from ideal. I started to look for other solutions and eventually found what I was looking for. I thought I'd share this here so that you could skip the headache.

# Prerequisites
* Obviously Node and npm should be installed
* You need to have a private account at npm. create an account <a href="https://www.npmjs.com/signup">here</a> if you don't have one already. and <a href="https://docs.npmjs.com/creating-a-new-npm-user-account#testing-your-new-account-with-npm-login">here</a> is how to login to npm in your local machine.
* Before you choose a name for your component or library, look for it in <a href="https://www.npmjs.com">npm</a> and see if it's available. if not, choose a different name or consider using a context. 

# Setup
* Create a new repository for your component, if you don't have one already, and clone it locally.
* At the root of your repo run `npm init` to create your package.json file.
* If not installed, install <a href="https://rollupjs.org/guide/en/">rollup</a> globally:
```
npm i -g rollup
```
* Create your basic file structure. for this example we will assume a `src` folder for the source files, and a `dist` folder for the build.
* Create your main component file. here we'll call it `src/ReactPublishGuide.jsx`.
* Install `react` and `react-dom` for development
```
npm i --save-dev react react-dom
```


# JSX bundler
We will use <a href="https://rollupjs.org/guide/en/">rollup</a>, a fast and clean js bundler which we have installed globally.
But first, let's install a plugin to handle our JSX and ES6:
```
npm i --save-dev @rollup/plugin-buble
```
Now let's add a `rollup.config.js` file to the root of the project:

```js
import buble from '@rollup/plugin-buble'

export default {
    input: 'src/ReactPublishGuide.jsx',
    output: {
        file: 'dist/ReactPublishGuide.js',
        format: 'cjs',
        exports: "default"
    },
    plugins: [buble()],
    external: ['react', 'react-dom']
};
```
Remember to replace `src/ReactPublishGuide.jsx` with your own component source file name and `dist/ReactPublishGuide.js` with the name that you want your build file to have.
if you use peer dependencies other then `react` and `react-dom` you should add them to the `external` array.

# .npmignore
An `.npmignore` file works just like a `.gitignore` and tells npm which files and folders should not be uploaded to the registry. any files that are used for your development but are not required for your component to work should be listed here. this includes all source files, demos and dev configs.
Add an `.npmignore` file to the root of your project:
```
src
rollup.config.js
```

# Peer dependencies
Peer dependencies are modules that your component may be using but should not be installed as part of your component.
At least `react` and `react-dom`, and probably `prop-types` should be listed as peer dependencies in your package.json file:
```js
{
  ...
  "peerDependencies": {
    "prop-types": "^15.6.0",
    "react": "^16.0.0",
    "react-dom": "^16.0.0"
  }
}
```
# Publish
To publish to npm, from the root of your project, run:
```
npm publish
```
When you publish again you will need to update the version number in your package.json file.








