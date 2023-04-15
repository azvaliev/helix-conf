# Requirements

## Multiple LSP & File Explorer

I am using a custom fork of the `helix` editor to add these features.
You can find it [here](https://github.com/azvaliev/helix) and follow the building from source
instruction on the official [documentation](https://docs.helix-editor.com/install.html#building-from-source)

## TypeScript w/ ESLint 

- [VSCode language servers extracted](https://github.com/hrsh7th/vscode-langservers-extracted)
- [TypeScript Language Servers](https://github.com/typescript-language-server/typescript-language-server)

**Cannot find tsconfig**

For me, my ESLint was having a rough time finding the `tsconfig.json`, and would often start looking in my src folder
It turns out there is one simple line which can help eslint know where to look for your `tsconfig.json`

```javascript
module.exports = {
  // ...
  parserOptions: {
    project: "./tsconfig.json",
    tsconfigRootDir: __dirname,
  }
}
```

The `tsconfigRootDir` option will tell ESLint to look for `tsconfig.json` relative to your `.eslintrc.js`.
