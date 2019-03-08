# TypeScript Starter
Example of a basic React/TypeScript project

I tried the TypeScript React Starter [] but tests in Jest didn't work. I then tried create-react-app --typescript and that seemed to be lacking compared to TypeScript React Starter. This project is a blend of the two.

Start with Create React App
```js
npx create-react-app proj-name --typescript
```
Eject
```js
yarn eject
```
Swap Yarn for npm
```js
rm -rf node_modules
rm yarn.lock
npm i
```
Modify config/paths.js by adding
```js
module.exports = {
  appTsLint: resolveApp('tslint.json'),
  appTsProdConfig: resolveApp('tsconfig.prod.json'),
  testsSetup: resolveModule(resolveApp, 'src/setupTests.ts'),
};
```
> The project currently does not have a tsline.json but will

> Also doesn't have a tsconfig.prod.json yet

> **Adding 'testsSetup' didn't seem to work. This may now be redundent**

Add & Delete files
```js
cd src
mkdir ui
cd ui
mkdir App
cd App
touch App.test.tsx App.tsx index.ts
cd ..
mkdir Hello
cd Hello
touch Hello.css Hello.test.tsx Hello.tsx index.ts
cd ..
rm App.css App.js App.test.js logo.svg serviceWorker.js
```
Rename index.js
```js
mv index.js index.tsx
```
Add setupTests.ts
```js
touch setupTests.ts
```
Add images.d.ts
```js
cd .. //now in root
touch images.d.ts
```

Add packages
```js
    "@types/enzyme": "^3.9.0",
    "@types/enzyme-adapter-react-16": "^1.0.5",
    "@types/jest": "^24.0.9",
    "@types/react": "^16.8.7",
    "@types/react-dom": "^16.8.2",
    "jest-environment-enzyme": "^7.0.2",
    "jest-enzyme": "^7.0.2",
    "typescript": "^3.3.3333",
```

**package.json changes**
Modify scripts to support absolute imports of components
```json
"scripts": {
    "start": "export NODE_PATH=src && node scripts/start.js",
    "build": "export NODE_PATH=src && node scripts/build.js",
    "test": "node scripts/test.js --modulePaths=src"
  },
```
Add to the Jest section
```json
    "setupTestFrameworkScriptFile": "jest-enzyme",
        "testEnvironment": "enzyme",
    "testEnvironmentOptions": {
      "enzymeAdapter": "react16"
    },
```

Add tsconfig.json and tslint.json
```js
touch tsconfig.json tslint.json
```