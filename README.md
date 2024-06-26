# Backend Project Setup

## Step 1: Install Node.js and npm

Ensure you have Node.js and npm installed on your machine. You can download them from the [official Node.js website](https://nodejs.org/).

## Step 2: Create a New Node.js Project

Open your terminal and create a new directory for your project. Navigate to the project directory.

```sh
mkdir my-ts-express-app
cd my-ts-express-app
```

## Step 3: Initialize a New Node.js Project

Run the following command to initialize a new Node.js project. This will create a package.json file.

```sh
npm init -y
```

Upon initializing a package.json file, the resultant file could resemble the snippet below:

```sh
{
  "name": "your-project-name",
  "version": "1.0.0",
  "description": "Your project description",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "Your Name",
  "license": "MIT"
}
```

## Step 4: Install TypeScript and Related Dependencies

Install TypeScript and other required dependencies:

```sh
npm install express
npm install -D @types/express typescript ts-node
```

- typescript: The TypeScript compiler.
- ts-node: Enables running TypeScript files directly with Node.js.
- @types/express: Provides TypeScript definitions for Express.

## Step 5: Create a tsconfig.json File

Create a tsconfig.json file in the project root to configure TypeScript.

```sh
{
  "compilerOptions": {
    "target": "esnext",
    "module": "commonjs",
    "lib": ["esnext"],
    "allowJs": true,
    "checkJs": false,
    "rootDir": "src",
    "strict": true,
    "esModuleInterop": true,
    "noImplicitAny": true,
    "resolveJsonModule": true,
    "outDir": "./dist"
  },
  "include": ["src/**/*.ts", "src/**/*.json", "src/**/*.graphql"],
  "exclude": ["node_modules"]
}
```

## Step 6: Create a Source Folder

Create a src folder in the project directory to store your TypeScript files.

```sh
mkdir src
```

## Step 7: Create an Express App in TypeScript

Inside the src folder, create an index.ts file with a basic Express setup:

```sh
// src/index.ts
import express from 'express';

const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.send('Hello, TypeScript with Express!');
});

app.listen(port, () => {
  console.log(`Server is running on http://localhost:${port}`);
});
```

## Step 8: Setup nodemon.json

Create a nodemon.json file to configure Nodemon:

```sh
{
  "ignore": [".git", "node_modules", "dist", "build"],
  "watch": ["src"],
  "exec": "npx ts-node ./src/index.ts",
  "ext": "ts"
}
```
## Step 9: Update the package.json File
Update the scripts section in your package.json file to include a start script that uses Nodemon to run your TypeScript code.

```sh
"scripts": {
  "start": "npx nodemon"
}
```

## Step 10: Run Your TypeScript Express App
You can now run your TypeScript Express app using the following command:

```sh
npm run dev
```