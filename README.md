# expo-nextjs-issue

## 🐛 Bug Report

### Environment

Expo CLI 3.4.1 environment info:
    System:
      OS: macOS 10.15
      Shell: 3.2.57 - /bin/bash
    Binaries:
      Node: 10.16.3 - /usr/local/bin/node
      Yarn: 1.19.1 - /usr/local/bin/yarn
      npm: 6.11.3 - /usr/local/bin/npm
    IDEs:
      Xcode: /undefined - /usr/bin/xcodebuild
    npmPackages:
      @types/react: ^16.8.23 => 16.9.9 
      @types/react-native: ^0.57.65 => 0.57.65 
      expo: ^35.0.0 => 35.0.0 
      react: 16.8.3 => 16.8.3 
      react-native: https://github.com/expo/react-native/archive/sdk-35.0.0.tar.gz => 0.59.8 
    npmGlobalPackages:
      expo-cli: 3.4.1

**App target: managed workflow, iOS, Android, but the problem is occurring for web (only when nextjs is set up).**

### Steps to Reproduce

<!--
  How would you describe your issue to someone who doesn’t know you or your project?
  Try to write a sequence of steps that anybody can repeat to see the issue.
  Be specific! If the bug cannot be reproduced, your issue may be closed.
-->

Create a new managed expo project, select the blank Typescript setup, [follow the steps](https://docs.expo.io/versions/latest/guides/using-nextjs/) to configure nextjs, and try to run it locally:

1. Run in terminal:
```
expo init bug
cd bug
npm i next --save
npm i @babel/plugin-proposal-decorators --save-dev
npm i expo-cli --save-dev
```

Open app.json and set expo.web.use to "nextjs" **(doing this causes the bug).**

### Expected Behavior

<!--
  How did you expect your project to behave?
  It’s fine if you’re not sure your understanding is correct.
  Just write down what you thought would happen.
-->

I would expect the project to start running in the browser and compile.

### Actual Behavior

The project fails to compile. First, it complains about `@expo/next-adapter` not existing, so I did:
`npm i @expo/next-adapter`.

After trying `expo start --web` again, I got this error (I replaced my path with path/to):

```
[ error ] /Users/path/to/expo-next-issue/node_modules/@expo/next-adapter/build/Document.js:3
import NextDocument, { Head, Main, NextScript } from 'next/document';
       ^^^^^^^^^^^^

SyntaxError: Unexpected identifier
    at Module._compile (internal/modules/cjs/loader.js:723:23)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:789:10)
    at Module.load (internal/modules/cjs/loader.js:653:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:593:12)
    at Function.Module._load (internal/modules/cjs/loader.js:585:3)
    at Module.require (internal/modules/cjs/loader.js:692:17)
    at require (internal/modules/cjs/helpers.js:25:18)
    at Object.@expo/next-adapter (/Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/external "@expo/next-adapter":1:1)
    at __webpack_require__ (/Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/webpack/bootstrap:21:1)
    at Module../pages/_document.js (/Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/pages/_document.js:1:1)
    at __webpack_require__ (/Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/webpack/bootstrap:21:1)
    at Object.0 (/Users/path/to/expo-next-issue/.next/server/static/development/pages/_document.js:118:18)
    at __webpack_require__ (/Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/webpack/bootstrap:21:1)
    at /Users/path/to/expo-next-issue/.next/server/static/development/pages/webpack:/webpack/bootstrap:89:1
    at Object.<anonymous> (/Users/path/to/expo-next-issue/.next/server/static/development/pages/_document.js:94:10)
    at Module._compile (internal/modules/cjs/loader.js:778:30)
/Users/path/to/expo-next-issue/node_modules/@expo/next-adapter/build/Document.js:3
```

<!--
  Did something go wrong?
  Is something broken, or not behaving as you expected?
  Describe this section in detail, and attach screenshots if possible.
  Don't just say "it doesn't work"!
-->

### Reproducible Demo

https://github.com/nandorojo/expo-nextjs-issue

```
git clone https://github.com/nandorojo/expo-nextjs-issue.git
cd expo-nextjs-issue
expo start --web
```

<!--
  Please share a project that reproduces the issue.
  There are two ways to do it:

    * Create a new app using https://snack.expo.io/ and try to reproduce the issue in it.
      This is useful if you roughly know where the problem is, or can’t share the real code.

    * Or, copy your app and remove things until you’re left with the minimal reproducible demo.
      This is useful for finding the root cause. You may then optionally create a Snack.

  This is a good guide to creating bug demos: https://stackoverflow.com/help/mcve
  Once you’re done, copy and paste the link to the Snack or a public GitHub repository below:
-->

<!--
  What happens if you skip this step?

  Someone will read your bug report, and maybe will be able to help you,
  but it’s unlikely that it will get much attention from the team. Eventually,
  the issue will likely get closed in favor of issues that have reproducible demos.

  Please remember that:

    * Issues without reproducible demos have a very low priority.
    * The person fixing the bug would have to do that anyway. Please be respectful of their time.
    * You might figure out the issues yourself as you work on extracting it.

  Thanks for helping us help you!
-->
