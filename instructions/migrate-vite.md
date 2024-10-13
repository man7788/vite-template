# Migrate to Vite from Create React App (CRA)

### Install Vite and all React related libraries (here: Vite's React Plugin) as development dependencies

```
npm install vite @vitejs/plugin-react --save-dev
```

### Uninstall create-react-app's dependency

```
npm uninstall react-scripts
```

### Adjust your `package.json` to use the following new scripts:

```
"scripts": {
"dev": "vite",
"build": "vite build",
"serve": "vite preview"
},
```

### Rename all extensions of files which are using JSX from ".js" to ".jsx",

### Create a vite.config.js file in your Vite + React project's root directory

```
touch vite.config.js
```

# Add the following implementation details to it. Essentially we want to keep the same output directory for the build as we had before with create-react-app. In addition, we want to use Vite's React Plugin

```
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig(() => {
  return {
    build: {
      outDir: 'build',
    },
    plugins: [react()],
  };
});
```

### Move the `public/index.html` into the project's root folder, because Vite expects it there

```
mv public/index.html .
```

### Remove all %PUBLIC_URL% occurrences in the index.html file

```
- <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />

* <link rel="icon" href="/favicon.ico" />

<!-- do this for all occurrences  -->
```

### Link the src/index.js file in your moved index.html file the following way

```
<body>
  <div id="root"></div>
  <script type="module" src="/src/index.jsx"></script>
</body>
```
