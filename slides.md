---
theme: apple-basic
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
mdc: true
---

# Pragmatisches Tooling

## Prettier, ESLint (9+) und Vite in 2025

---

## layout: two-cols

# 1. Grundlagen

::right::

<!-- <img src="/api/placeholder/500/300" alt="Code quality tools illustration" class="rounded shadow" /> -->

---

# Linting vs. Formatting

| **Linting**                          | **Formatting**                           |
| ------------------------------------ | ---------------------------------------- |
| Findet semantische/logische Probleme | Kümmert sich um die Formatierung         |
| Identifiziert problematische Muster  | Sorgt für einheitliches Erscheinungsbild |
| Tools: ESLint                        | Tools: Prettier                          |

---

# Statische vs. Dynamische Analyse

| **Statisch**                             | **Dynamisch**                                |
| ---------------------------------------- | -------------------------------------------- |
| Prüft ohne Ausführung                    | Prüft während der Laufzeit                   |
| Findet: Syntaxfehler, Stilverstöße, Bugs | Findet: Laufzeitfehler, Performance-Probleme |
| Schnell, im Editor oder CI               | Braucht echte Eingaben oder Tests            |
| Beispiele: ESLint, TypeScript            | Beispiele: Profiler, Debugger, Tests         |

---

# Warum brauchen wir das?

> "Our top reason was to stop wasting our time debating style nits."
>
> _prettier.io_

- Keine Diskussionen über Tabs vs. Spaces
- Fokus auf Logik statt Formatierung
- Konsistente Codequalität
- Einfacheres Onboarding

---

## layout: section

# 2. Tool-Landschaft

---

# JavaScript/TypeScript Ecosystem

- **ESLint**: De-facto Standard für JS/TS-Linting
- **Prettier**: Opinionated Formatter für diverse Sprachen
- **TypeScript Compiler**: Eigenes Typechecking/Linting
- **JSConfig**: VS Code-Integration für JavaScript

---

# PHP/Laravel Ecosystem

- **PHP_CodeSniffer**: Klassischer PHP-Linter
- **PHP-CS-Fixer**: PHP-Formatter mit PSR-Standards
- **Pint**: Laravel-spezifischer Formatter
- **Duster**: Kombiniert verschiedene Tools
- **Larastan/PHPStan**: Statische Analyse

---

# Build-Tools mit Linting

- **Vite**: Modernes, schnelles Build-Tool
- **Laravel Mix**: Wrapper um Webpack

---

## layout: section

# 3. Prettier

## Konsistente Codeformatierung

---

# Was ist Prettier?

- Opinionated Code-Formatierer
- Unterstützt JavaScript, TypeScript, CSS, HTML, JSON, Vue...
- 2025: Mehr Sprachen, bessere Konfigurierbarkeit

<div class="grid grid-cols-2 gap-4 mt-4">
  <div class="bg-gray-100 p-4 rounded">
    <h3 class="text-sm mb-2">Vor Prettier</h3>
    <pre>
function Example(props)    {
  if(props.isEnabled){
    return <div>Enabled</div>}
  else{
      return <div>Disabled</div>
  }
}
    </pre>
  </div>
  <div class="bg-gray-100 p-4 rounded">
    <h3 class="text-sm mb-2">Nach Prettier</h3>
    <pre>
function Example(props) {
  if (props.isEnabled) {
    return <div>Enabled</div>;
  } else {
    return <div>Disabled</div>;
  }
}
    </pre>
  </div>
</div>

---

# Warum Prettier?

- Zeit sparen
- Code Reviews verbessern
- Konsistenz im Team
- Einfacheres Onboarding

---

# Einrichtung in VSCode

```json
// .prettierrc
{
  "printWidth": 100,
  "tabWidth": 2,
  "singleQuote": true,
  "trailingComma": "es5",
  "semi": true
}

// settings.json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode"
}
```

---

## layout: section

# 4. ESLint 9+

## Code-Qualität sicherstellen

---

# Was ist ESLint?

- Statisches Analyse-Tool für JavaScript
- Findet und behebt Probleme
- ESLint 9+: Flat Config, bessere Performance

---

# Warum ESLint?

- Fehler frühzeitig erkennen
- Best Practices erzwingen
- Modernisierung fördern
- Lerneffekt für Entwickler

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

## layout: section

# 5. Vite

## Blitzschnelle Entwicklungsumgebung

---

# Was ist Vite?

- Modernes Build-Tool und Dev-Server
- Optimiert für ESM (ECMAScript Modules)
- 2025: Noch bessere Performance, mehr Plugins

---

# Warum Vite?

- Extreme Geschwindigkeit
- Einfache Konfiguration
- Instant Hot Module Replacement
- Optimierte Production Builds

---

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

# 6. Integration

## Zusammenspiel in VSCode

---

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

# Empfohlene Extensions

- Prettier
- ESLint
- Vite Helper
- Error Lens

---

## layout: section

# 7. Umgang mit Problemfällen

---

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

# Prettier-Formatierung überspringen

```js
// Ganzes File
// prettier-ignore-file

// Codeblock
// prettier-ignore
const matrix = [
  1, 0, 0,
  0, 1, 0,
  0, 0, 1
];

// In JSX/Vue Templates
{/* prettier-ignore */}
<div>Dies wird nicht formatiert!</div>;
```

---

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
{{# prettier-ignore #}}
  {{ komplexer_antlers_code }}
{{# /prettier-ignore #}}
```

---

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

# 8. Implementierungsstrategie

---

# Schrittweise Einführung

1. **Analyse**: Codebase bewerten
2. **Planung**: Regeln & Konfigurationen festlegen
3. **Einführung**: Tools schrittweise integrieren
4. **Schulung**: Team trainieren
5. **Iteration**: Regeln anpassen nach Bedarf

---

# Umgang mit Legacy-Code

- Migration nach Priorität
- Automatische Fixes für einfache Probleme
- Manuelle Anpassungen für komplexe Fälle
- Verzeichnisspezifische Overrides

---

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

# 9. Vorteile

---

# Messbare Vorteile

- 20-30% weniger Zeit in Code Reviews
- Weniger Fehler in Produktion
- Schnellere Entwicklungszyklen
- Höhere Codequalität

---

# Nicht-messbare Vorteile

- Höhere Entwicklerzufriedenheit
- Einfacheres Onboarding
- Weniger Frustration
- Einheitliche Qualitätsstandards

---

## layout: section

# 10. Nächste Schritte

---

# Implementierungsplan

1. **Woche 1-2**: Setup & Konfiguration
2. **Woche 3-4**: Pilotprojekt & Anpassung
3. **Woche 5-6**: Ausweitung auf alle Projekte
4. **Fortlaufend**: Regelmäßige Verbesserungen

---

# Lernressourcen

- [Prettier Docs](https://prettier.io/docs/en/)
- [ESLint Docs](https://eslint.org/docs/latest/)
- [Vite Docs](https://vitejs.dev/guide/)
- [Awesome ESLint](https://github.com/dustinspecker/awesome-eslint)
- [Awesome Vite](https://github.com/vitejs/awesome-vite)

---

## layout: end

# Fragen?
