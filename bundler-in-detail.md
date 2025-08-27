## Bundler functions

1. __Tree Shaking__: removes unused code/files.
2. __Minification__: removes whitespace, comments to reduce file size.
3. __Uglification__: renames variables to shorter names for smaller files.
4. __Transpilation__: converts code for browser compatibility.
5. __Bundling__: is just the action/process of combining multiple files into fewer bundles.
6. __Code Splitting__ enables __lazy loading__ by:
- Bundler splits code into separate chunks
- Main bundle loads first
- Additional chunks load on demand (lazy loading)
- Common pattern: route-based splitting, dynamic imports
Example: ```import('./module.js').then(...)``` creates a separate chunk that loads only when called.
Lazy loading is a runtime behavior, and code splitting is a bundler feature that enables it.
__Lazy Loading__ = loads only what's immediately needed.

## Details 
1. __Uglification__ is for file size reduction, not security/encryption. Client-side code is always accessible regardless of these optimizations.
2. __Transpilation__ converts:
- ES6+ → ES5 (older browser support).
- TypeScript → JavaScript.
- JSX → JavaScript (React syntax).
- Modern syntax → Compatible syntax (async/await, arrow functions, etc.).
- __Most common__: Modern JS features down to versions that older browsers understand.
