# 🌳 Tree sitter implementation for rego language

This repository tries to cover the tree-sitter implementation for the [OPA Rego language](https://www.openpolicyagent.org/docs/latest/policy-language/)

You can use [NVM](https://github.com/nvm-sh/nvm) in order to load the Node version used to develop the grammar by issuing `nvm use`
Available scripts

```bash
yarn generate # initializes parsing for the grammar.js file
yarn build # compiles the tree-sitter grammar
```

Please, verify that your editor supports [EditorConfig plugin](https://editorconfig.org/), which is necessary to keep the development consistent.
This repository uses Github Actions, which help verify that the changes submitted can be unit-tested, built and deployed to a [Github Pages](https://fallenangel97.github.io/tree-sitter-rego/)

List of TODO items:
- Introduce more unit tests covering the internal functions
- Add locals.scm

## Local testing in browser

```
npx tree-sitter build-wasm
npx tree-sitter playground
```

This will open locally http://127.0.0.1:8000/, where you can check your rules
directly in the browser

## Local testing in NeoVim
To be able to locally verify the changes - you should modify your `init.lua` file
to point to your locally installed tree-sitter grammar

```lua
local parser_config = require "nvim-treesitter.parsers".get_parser_configs()

parser_config.rego = {
  install_info = {
    url = "/home/user/Documents/tree-sitter-rego", -- local path or git repo
      files = {"src/parser.c"},
    -- optional entries:
      branch = "master", -- default branch in case of git repo if different from master
      generate_requires_npm = false, -- if stand-alone parser without npm dependencies
      requires_generate_from_grammar = false, -- if folder contains pre-generated src/parser.c
  },
  filetype = "rego", -- if filetype does not match the parser name
}
```

The live playground is available at: https://fallenangel97.github.io/tree-sitter-rego/

---
Powered by

<a href='https://decodeapps.pp.ua/'><img height="20" src="https://decodeapps.pp.ua/_next/static/media/logo-light.3763f5cc.svg" /></a>
