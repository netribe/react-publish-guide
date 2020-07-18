# react-publish-guide
This is a simple guide for publishing react components to npm.

# Why
I've recently started publishing small, reusable React components to npm and after trying to do this with the tools that I'm used to, I've found that the process was far from ideal. I started to look for other solutions and eventually found what I was looking for. I thought I'd share this here so that you could skip the headache.

# Prerequisites
* Obviously Node and npm should be installed
* You need to have a private account at npm. create an account <a href="https://www.npmjs.com/signup">here</a> if you don't have one already. and <a href="https://docs.npmjs.com/creating-a-new-npm-user-account#testing-your-new-account-with-npm-login">here</a> is how to login to npm in your local machine.

# Setup
* Create a new repository for your component, if you don't have one already, and clone it locally.
* If not installed, install <a href="https://rollupjs.org/guide/en/">rollup</a> globally:
```
npm i -g rollup
```
* Create your basic file structure. for this example we will assume a `src` folder for the source files, and a `dist` folder for the build.









