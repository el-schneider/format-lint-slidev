---
theme: ./theme
background: https://source.unsplash.com/collection/94734566/1920x1080
highlighter: shiki
mdc: true
layout: intro
---

## hello vvworld

# Prettier & ESLint

<v-click>& Pint, Duster, Larastan, …</v-click>

---
layout: section
---

# Was erwartet euch heute?

<v-clicks>

- Grundlagen: Formatting, Linting, … — _die Terminologie verstehen_
- Überblick über das Ökosystem — _die Tools kennen_
- Grundlegendes Setup und How-To der wichtigsten Tools
  - Extensions
  - Config Dateien
  - CLI Befehle
- Die Tools souverän nutzen — _sich nicht ärgern lassen_

</v-clicks>

---
layout: statement
---

# Formatting/Linting ist das IaC für die Codequalität

---
layout: section
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Grundlagen

---
layout: two-cols-header
---

# Was macht Formatting?

- Automatische Anpassung der Code-Struktur nach vordefinierten Regeln
- Einheitliches Erscheinungsbild des Codes sicherstellen
- Änderung von Whitespace, Zeilenumbrüchen, Einrückungen, Kommasetzung etc.

::left::

<v-click>

## Vorher

```php
<?   php

echo     'Bad!'   ;

if        (    $bad){
echo "Bad";
       }
```

</v-click>

::right::

<v-click>

## Nachher

```php
<?php

echo "Less bad!";

if ($lessBad) {
    echo "Less bad";
}
```

</v-click>

---
layout: bullets
---

# Was macht Linting?

- Statische Code-Analyse zur Identifikation problematischer Muster
- Logische Fehler, Bugs vor der Ausführung finden
- Tools scannen Code ohne Ausführung und warnen bei Problemen

---
layout: bullets
---

# Formatting vs. Linting

| **Formatting**                                             | **Linting**                                                      |
| ---------------------------------------------------------- | ---------------------------------------------------------------- |
| Erzwingt einheitlichen Code-Stil                           | Analysiert Code auf potenzielle Fehler und Qualitätsprobleme     |
| Fokus auf Syntax-Darstellung (Leerzeichen, Einrückung ...) | Fokus auf Code-Semantik, Logik und Best Practices                |
| Formatiert Code automatisch nach Stilregeln                | Kann einige Probleme beheben, meldet aber hauptsächlich Probleme |
| Analysiert Codestruktur ohne Logikprüfung                  | Versteht Code-Bedeutung und potenzielle Ausführungspfade         |
| Erkennt keine Logikfehler oder Bugs                        | Identifiziert potenzielle Bugs, Code Smells und Anti-Patterns    |
| Generell schneller - einfachere Operationen                | Intensiver - erfordert tiefere Analyse                           |

---
layout: bullets
---

# Statische vs. Dynamische Analyse

| **Statisch**                             | **Dynamisch**                                |
| ---------------------------------------- | -------------------------------------------- |
| Prüft ohne Ausführung                    | Prüft während der Laufzeit                   |
| Findet: Syntaxfehler, Stilverstöße, Bugs | Findet: Laufzeitfehler, Performance-Probleme |
| Schnell, im Editor oder CI               | Braucht echte Eingaben oder Tests            |
| Beispiele: ESLint, TypeScript            | Beispiele: Profiler, Debugger, Tests         |

---
layout: two-cols-header
---

# Abstract Syntax Tree

- Beide Toolgruppen verwenden üblicherweise einen AST
- Viele Tools mach(t)en deswegen sowohl Linting als auch Formatting

::left::

## Code

```php
<?php

echo "hello vvworld!";
```

::right::

## AST (gekürzt)

```json
{
  "kind": "program",
  "children": [
    {
      "expressions": [
        {
          "kind": "string",
          "raw": "\"hello vvworld!\"",
          "isDoubleQuote": true
        }
      ]
    }
  ]
}
```

---
src: ./tool-landscape.md
---

layout: bullets

---
layout: bullets
---

# Uff …

---
layout: statement
---

# It's not about looks

oder: Das _Wie_ ist Nebensache

---
layout: bullets
---

# Worum geht es dann?

> "Our top reason was to stop wasting our time debating style nits."
>
> _prettier.io_

> "Prettier determines our code style. While Prettier's output isn't always the prettiest, it's consistent and removes all (meaningless) discussion about code style."
>
> _spatie.be_

> You can avoid discussions like "should I be using tabs or spaces?" and "does the curly brace go at the end of the line or on the next line?"
>
> _vicvijayakumar.com_

---
layout: bullets
---

# Was wir davon haben

- Fokus auf Logik statt Formatierung – _Konzentration auf das Wesentliche_
- Lesbarere Merge Requests – _das wichtige auf einen Blick_
- Effizientere Pipelines – _kein `fix: linting` mehr_
- Einfacheres Onboarding – _neue Teammitglieder können sofort produktiv sein_
- Als Hilfestellung für Azubis – _so muss das also aussehen_
- Weniger Diskussionen – _lasst die Tools entscheiden_

---
layout: statement
---

# Wir haben das schon längst

---
layout: bullets
---

# JavaScript/TypeScript Ecosystem

- **ESLint**: De-facto Standard für JS/TS-Linting
- **Prettier**: Opinionated Formatter für diverse Sprachen
- **TypeScript Compiler**: Eigenes Typechecking/Linting

---
layout: section
---

# Prettier

## Konsistente Codeformatierung ohne Diskussion

---
layout: image-right
image: /images/prettier_splash.png
---

# Was ist Prettier?

- _Opinionated_ Code-Formatierer
- Unterstützt JavaScript, TypeScript, CSS, HTML, PHP, …
- De-facto Standard für JavaScript/TypeScript

---
layout: two-cols-header
---

# Language Support

::left::

- JavaScript/TypeScript
- JSX
- Vue
- CSS, Less, and SCSS
- HTML
- JSON
- GraphQL
- Markdown
- YAML
- ...

::right::

## Offizielle Plugins

Prettier hat viele Plugins für verschiedene Sprachen und Frameworks.

```bash
npm install --save-dev prettier-plugin-tailwindcss
```

- `prettier-plugin-blade`
- `prettier-plugin-tailwindcss`
- `prettier-plugin-antlers`
- `prettier-plugin-php`
- `prettier-plugin-xml`

---
layout: two-cols-header
---

# Installation im Projekt

::left::

## 1. Prettier installieren:

```bash
npm install --save-dev prettier
```

::right::

## 2. Prettier konfigurieren:

```json
// .prettierrc
{
  "printWidth": 100,
  "tabWidth": 2,
  "singleQuote": true,
  "trailingComma": "es5",
  "semi": true
}
```

```json
// settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
  //
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

---
layout: two-cols-header
---

# Einrichtung in VSCode

::left::

- Installiere die Extension: <br>
  `esbenp.prettier-vscode`
- Optional: `editor.formatOnSave` in VSCode

```bash
npm install --save-dev prettier
```

::right::

```json
// settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

---
layout: two-cols-header
---

# Nutzung in der Pipeline

::left::

## CLI Befehl

```bash
prettier [options] [file/dir/glob ...]
```

## Empfehlung

In der Pipeline nur checken, nicht fixen.

::right::

## Alles oder einzelne Dateien

```bash
prettier --check .
```

```bash
prettier --write examples/example.blade.php
```

## Als NPM Script

```bash
npm run format:check
npm run format:fix
```

```json
"scripts": {
  "format:check": "prettier --check .",
  "format:fix": "prettier --write ."
}
```

---
layout: two-cols-header
---

# Notfall-Maßnahmen

oder: bitte, nerv' mich nicht!

::left::

## .prettierignore

Beispiel im `stinit`:

```bash
# .prettierignore
**/*.yml
**/*.yaml
**/*.md
/storage
composer.lock
composer.json
package-lock.json
/public/vendor
```

```bash
# einzelne Dateien ignorieren
/examples/example.blade.php
```

::right::

## Ignorieren mit Kommentaren

```js
// JS
// prettier-ignore
const matrix = [
  1, 0, 0,
  0, 1, 0,
  0, 0, 1
];
```

```css
// CSS
/* prettier-ignore */
.my    ugly rule {
}
```

```yaml
// YAML
# prettier-ignore
key  : value
hello: world
}
```

---
layout: section
---

# ESLint 9+

## Code-Qualität sicherstellen

---
layout: bullets
---

# Was ist ESLint?

- Statisches Analyse-Tool für JavaScript
- Findet und behebt Probleme
- ESLint 9+: Flat Config, bessere Performance

---
layout: bullets
---

# Warum ESLint?

- Fehler frühzeitig erkennen
- Best Practices erzwingen
- Modernisierung fördern
- Lerneffekt für Entwickler

---
layout: bullets
---

# Moderne Konfiguration (ESLint 9+)

```js
// eslint.config.js
import js from "@eslint/js";
import tseslint from "typescript-eslint";

export default [
  js.configs.recommended,
  ...tseslint.configs.recommended,
  {
    files: ["**/*.js", "**/*.ts", "**/*.tsx"],
    rules: {
      "no-unused-vars": "error",
      "no-console": "warn",
      // Teamspezifische Regeln hier
    },
  },
];
```

---

## layout: bullets

# VSCode-Integration

```json
// settings.json
{
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

---
layout: bullets
---

# PHP/Laravel Ecosystem

- **PHP_CodeSniffer**: Klassischer PHP-Linter
- **PHP-CS-Fixer**: PHP-Formatter mit PSR-Standards
- **Pint**: Laravel-spezifischer Formatter
- **Duster**: Kombiniert verschiedene Tools
- **Larastan/PHPStan**: Statische Analyse

---

## layout: section

# Vite

## Blitzschnelle Entwicklungsumgebung

---

## layout: bullets

# Was ist Vite?

- Modernes Build-Tool und Dev-Server
- Optimiert für ESM (ECMAScript Modules)
- 2025: Noch bessere Performance, mehr Plugins

---

## layout: bullets

# Warum Vite?

- Extreme Geschwindigkeit
- Einfache Konfiguration
- Instant Hot Module Replacement
- Optimierte Production Builds

---

## layout: bullets

# Einrichtung eines Projekts

```bash
npm create vite@latest
```

```js
// vite.config.js
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
    open: true,
  },
  build: {
    minify: "terser",
    sourcemap: true,
  },
});
```

---

## layout: section

# Integration

## Zusammenspiel in VSCode

---

## layout: bullets

# Workspace-Konfiguration

```json
// .vscode/settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "eslint.validate": [
    "javascript",
    "typescript",
    "javascriptreact",
    "typescriptreact"
  ],
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[typescript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

---

## layout: bullets

# Empfohlene Extensions

- Prettier
- ESLint
- Antlers Toolbox

---

## layout: section

# Umgang mit Problemfällen

---

## layout: bullets

# ESLint-Regeln deaktivieren

```js
// Für eine Zeile
const foo = ""; // eslint-disable-line no-unused-vars

// eslint-disable-next-line no-console
console.log("Nur hier erlaubt");

// Für einen Bereich
/* eslint-disable */
function legacyFunction() {
  // Problematischer Code...
}
/* eslint-enable */

// Spezifische Regeln
/* eslint-disable no-console, no-unused-vars */
function debuggingFunction() {
  const debugVar = "helper";
  console.log("Debug info");
}
/* eslint-enable no-console, no-unused-vars */
```

---

## layout: bullets

# Laravel & Blade Lösungen

```js
// ESLint für Blade
export default [
  {
    files: ['**/*.blade.php'],
    processor: '@eslint-community/eslint-plugin-php/processors/blade',
    // Spezielle Regeln
  }
];

// Prettier mit Blade-Plugin
{
  "plugins": ["@shufo/prettier-plugin-blade"],
  "overrides": [
    {
      "files": "*.blade.php",
      "options": {
        "parser": "blade",
        "tabWidth": 4
      }
    }
  ]
}
```

---

## layout: bullets

# Antlers (Statamic) Lösungen

```json
// settings.json
{
  "[antlers]": {
    "editor.formatOnSave": false
  }
}
```

```
{{ komplexer_antlers_code }}
```

---

## layout: bullets

# .ignore Dateien

```
# .eslintignore
src/legacy-components/**/*
vendor/**/*
node_modules/**/*
*.min.js

# .prettierignore
/vendor
/node_modules
*.blade.php
*.min.js
dist/*
```

---

## layout: section

# Implementierungsstrategie

---

## layout: bullets

# Schrittweise Einführung

1. **Analyse**: Codebase bewerten
2. **Planung**: Regeln & Konfigurationen festlegen
3. **Einführung**: Tools schrittweise integrieren
4. **Schulung**: Team trainieren
5. **Iteration**: Regeln anpassen nach Bedarf

---

## layout: bullets

# Umgang mit Legacy-Code

- Migration nach Priorität
- Automatische Fixes für einfache Probleme
- Manuelle Anpassungen für komplexe Fälle
- Verzeichnisspezifische Overrides

---

## layout: bullets

# CI/CD-Integration

```yaml
# .github/workflows/lint.yml
name: Lint

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: "20"
      - run: npm ci
      - run: npm run lint
```

---

## layout: section

# Vorteile

---

## layout: bullets

# Messbare Vorteile

- 20-30% weniger Zeit in Code Reviews
- Weniger Fehler in Produktion
- Schnellere Entwicklungszyklen
- Höhere Codequalität

---

## layout: bullets

# Nicht-messbare Vorteile

- Höhere Entwicklerzufriedenheit
- Einfacheres Onboarding
- Weniger Frustration
- Einheitliche Qualitätsstandards

---

## layout: section

# Nächste Schritte

---

## layout: bullets

# Implementierungsplan

1. **Woche 1-2**: Setup & Konfiguration
2. **Woche 3-4**: Pilotprojekt & Anpassung
3. **Woche 5-6**: Ausweitung auf alle Projekte
4. **Fortlaufend**: Regelmäßige Verbesserungen

---

## layout: bullets

# Lernressourcen

- [Prettier Docs](https://prettier.io/docs/en/)
- [ESLint Docs](https://eslint.org/docs/latest/)
- [Vite Docs](https://vitejs.dev/guide/)
- [Awesome ESLint](https://github.com/dustinspecker/awesome-eslint)
- [Awesome Vite](https://github.com/vitejs/awesome-vite)

---

## layout: section

# Fragen?
