# Vitest with React Testing Library

### Install Vitest on the command line:

```
npm install vitest --save-dev
```

### Then in your `package.json` file, add another script which will run the tests eventually

```
{
  ...
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "test": "vitest",
    "preview": "vite preview"
  },
  ...
}
```

### Create a test file somewhere in your project with the suffix test, e.g. App.test.jsx, and give it the following content

```
import { describe, it, expect } from 'vitest';

describe('something truthy and falsy', () => {
  it('true to be true', () => {
    expect(true).toBe(true);
  });

  it('false to be false', () => {
    expect(false).toBe(false);
  });
});
```

### Install the library on the command line

Since React Testing Library tests React components, we need to enable HTML in Vitest with a library like jsdom.

```
npm install jsdom --save-dev
```

### Include it to the Vite configuration file

```
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    environment: 'jsdom',
  },
});
```

### Install React Testing Library on the command line

```
npm install @testing-library/react @testing-library/jest-dom --save-dev
```

### Add a test setup file in tests/setup.js and give it the following implementation

```
import { expect, afterEach } from 'vitest';
import { cleanup } from '@testing-library/react';
import * as matchers from "@testing-library/jest-dom/matchers";

expect.extend(matchers);

afterEach(() => {
  cleanup();
});
```

### Include this new test setup file in Vite's configuration file

In addition, make all imports from Vitest global, so that you don't need to perform these imports (e.g. expect) in each file manually anymore

```
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [react()],
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: './tests/setup.js',
  },
});
```

### You can render React components in Vitest now

```
import { render, screen } from '@testing-library/react';

import App from './App';

describe('App', () => {
  it('renders headline', () => {
    render(<App title="React" />);

    screen.debug();

    // check if App components renders headline
  });
});
```

### There’s one more tiny package to install before we can begin

```
npm install @testing-library/user-event --save-dev
```
