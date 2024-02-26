# helix config

## How to setup?

1. Install Helix - [docs.helix-editor.com](https://docs.helix-editor.com/install.html)
1. Clone this into your `~/.config/helix` folder.
1. `hx --grammar fetch` + `hx --grammar build` to get all the nice autocomplete stuff
1. For the file manager, see below for the `lf-pick` setup
1. Check `hx --health` to make sure you have the LSP's you need installed
1. Profit?!!

## `lf-pick` helix file manager

Requires [lf](https://github.com/gokcehan/lf?tab=readme-ov-file#installation)

Drop this file somewhere which your PATH will pick up, name it `lf-pick` and make sure it's executable `chmod +x lf-pick`
```bash
function lfp(){
  local TEMP=$(mktemp)
  lf -selection-path=$TEMP
  echo >> $TEMP
  while read -r line
  do
    echo "$line"
  done < "$TEMP"
}

lfp
```

Now you can use `-` when in normal mode in your editor 

## TypeScript w/ ESLint 

Need to install:
- [VSCode language servers extracted](https://github.com/hrsh7th/vscode-langservers-extracted)
- [TypeScript Language Servers](https://github.com/typescript-language-server/typescript-language-server)

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

