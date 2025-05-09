# Snippets

## EditorConfig

```ini
root = true

[*]
charset = utf-8
end_of_line = lf
indent_size = 4
indent_style = space
insert_final_newline = true
trim_trailing_whitespace = true

[*.{yaml,yml}]
indent_size = 2

[*.md]
trim_trailing_whitespace = false
```

## Prettier

### Installation

```bash
npm install --save-dev \
    prettier \
    prettier-plugin-antlers \
    prettier-plugin-tailwindcss
```

### Config

```json
{
  "singleQuote": true,
  "printWidth": 120,
  "plugins": [
    "prettier-plugin-antlers",
    "prettier-plugin-tailwindcss"
  ],
  "overrides": [
    {
      "files": ["*.antlers.*"],
      "options": {
        "parser": "antlers"
      }
    }
  ]
}
```

### Ignore

```json
**/*.yml
**/*.yaml
**/*.md
/storage
composer.lock
composer.json
package-lock.json
/public/vendor
```

## Prettier VSCode

### Installation

```bash
code --install-extension esbenp.prettier-vscode
```

### Config

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

## ESLint

### Installation

```bash
npm install --save-dev eslint globals
```

### Config

```js
import { includeIgnoreFile } from "@eslint/compat";
import { fileURLToPath } from "node:url";
import { defineConfig } from "eslint/config";
import js from "@eslint/js";
import globals from "globals";

const gitignorePath = fileURLToPath(
  new URL(".gitignore", import.meta.url),
);

export default defineConfig([
  js.configs.recommended,
  includeIgnoreFile(gitignorePath),
  {
    languageOptions: {
      globals: {
        ...globals.browser,
        ...globals.node,
      },
    },
  },
]);
```

## ESLint VSCode

### Installation

```bash
code --install-extension dbaeumer.vscode-eslint
```

### Config

```json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

## CLI

### Prettier

```bash
npx prettier [options] [file|dir|glob]*
```

#### Checken

```bash
prettier . --check
```

#### Fixen

```bash
prettier . --write
```

### ESLint

```bash
npx eslint [options] [file|dir|glob]*
```

#### Checken

```bash
npx eslint .
```

#### Fixen

```bash
npx eslint . --fix
```
