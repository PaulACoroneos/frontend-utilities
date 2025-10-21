# frontend-utilities

My custom front end utilities I've written as practice

## Setup

This project uses Vite for building and Vitest for testing JavaScript utilities.

### Prerequisites

- Node.js (v14 or higher recommended)
- npm or yarn

### Installation

```bash
npm install
```

## Project Structure

```
frontend-utilities/
├── src/
│   └── index.js          # Main entry point - export your utilities here
├── tests/
│   └── example.test.js   # Test files
├── vite.config.js        # Vite configuration
├── vitest.config.js      # Vitest configuration
└── package.json
```

## Available Scripts

### Development
```bash
npm run dev              # Start Vite dev server
```

### Building
```bash
npm run build           # Build the library for production
```

### Testing
```bash
npm test                # Run tests in watch mode
npm run test:run        # Run tests once
npm run test:ui         # Run tests with UI
npm run coverage        # Run tests with coverage report
```

## Adding Your Utilities

1. Create your utility functions in the `src/` directory
2. Export them from `src/index.js`
3. Write tests in the `tests/` directory

### Example

**src/debounce.js:**
```javascript
export function debounce(func, wait) {
  let timeout;
  return function executedFunction(...args) {
    const later = () => {
      clearTimeout(timeout);
      func(...args);
    };
    clearTimeout(timeout);
    timeout = setTimeout(later, wait);
  };
}
```

**src/index.js:**
```javascript
export { debounce } from './debounce.js';
```

**tests/debounce.test.js:**
```javascript
import { describe, it, expect, vi } from 'vitest';
import { debounce } from '../src/debounce.js';

describe('debounce', () => {
  it('should debounce function calls', () => {
    // Your test implementation
  });
});
```

## Configuration

### Vite
The `vite.config.js` file is configured to build the library in both ES and UMD formats.

### Vitest
The `vitest.config.js` file is configured with:
- Node environment
- Global test APIs (describe, it, expect, etc.)
- Coverage reporting with v8 provider

## License

ISC
