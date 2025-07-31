# helix config

## How to setup?

1. Install Helix - [docs.helix-editor.com](https://docs.helix-editor.com/install.html)
1. Clone this into your `~/.config/helix` folder.
1. `hx --grammar fetch` + `hx --grammar build` to get all the nice autocomplete stuff
1. For the file manager, see below for the `lf-pick` setup
1. Check `hx --health` to make sure you have the LSP's you need installed
1. Profit?!!

## TypeScript w/ ESLint 

Need to install:
- [VSCode language servers extracted](https://github.com/hrsh7th/vscode-langservers-extracted).  
    IMPORTANT: use version 4.8.0, newer version seems to break
- [VTSLS](https://github.com/yioneko/vtsls)

### Cannot find tsconfig error

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

