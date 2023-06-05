# **Code Quality Tools**

## **Table of Contents**

- [**Code Quality Tools**](#code-quality-tools)
  - [**Table of Contents**](#table-of-contents)
  - [**Prettier**](#prettier)
    - [**Abstract**](#abstract)
    - [**VSCode Settings**](#vscode-settings)
      - [**Editorconfig**](#editorconfig)
    - [**Prettier Settings**](#prettier-settings)
  - [**ESLint**](#eslint)
    - [**Abstract**](#abstract-1)
    - [**Recommended Plugins**](#recommended-plugins)
  - [**CSpell**](#cspell)
    - [**Abstract**](#abstract-2)
  - [**Other Tools**](#other-tools)
  - [](#)

## **Prettier**

[Prettier](https://prettier.io/ "Open") is the base code formatter used throughout our projects (in combination with some help from the IDE through common settings, and shared linting rules). Through the shared `@falkor/falkor-prettier-config` NPM workspace, the rules (and versions) are handled independently, and can be extended on will inside descendant configurations.

> _The shared Prettier configuration is part of our Custom Visual Templates._

### **Abstract**

- Prettier enforces consistent code style.
  - Performs formatting that won't affect the AST.
  - Re-prints parsed AST with its own rules.
- Prettier is [opinionated](https://prettier.io/docs/en/option-philosophy.html "Open"), there are not many settings that can be changed.
  - Fewer meetings about style. 🚀
- Prettier integrates in the IDE, but can be set up as project dependency.
  - Can use lightweight IDE with no Prettier integration.
  - Can be run separately from shell:
    - As packaging hook (early fail)
    - As version control hook (automated code review workflow)
- Industry standard, integrates well with linters.

  - Linters use the AST to make language specific analysis.
  - [ESLint](#eslint "View") has specific ruleset to turn off its formatting rules in favor of Prettier.

### **VSCode Settings**

Common VSCode settings used in combination with Prettier:

| Setting                  | Value    | Comment          | In Prettier |
| :----------------------- | :------- | :--------------- | :---------- |
| End Of Line (EOL)        | `\n`     | Line Feed (`LF`) | ✔️          |
| Tab Size                 | `4`      | Use Spaces       | ✔️          |
| Semicolon                | `insert` |                  | ✔️          |
| Quote Style              | `double` |                  | ✔️          |
| Insert Spaces            | `true`   |                  | ❌          |
| Trim Trailing Whitespace | `true`   |                  | ❌          |
| Insert Final Newline     | `true`   |                  | ❌          |

> _The shared VSCode configuration is part of our Custom Visual Templates._

#### **Editorconfig**

Common `.editorconfig` values collected during research (for use with `IDEA` / `WebStorm`):

```conf
root = true

[*]
end_of_line = lf
trim_trailing_whitespace = true
insert_final_newline = true
indent_style = space
indent_size = 4
quote_type = double
spaces_around_operators = true

[*.{html,css,less,json,jsonc,yml,md}]
indent_style = space
indent_size = 2

[*.md]
trim_trailing_whitespace = false
```

### **Prettier Settings**

Common Prettier settings:

| Setting           | Value    | Comment                               |
| :---------------- | :------- | :------------------------------------ |
| End Of Line (EOL) | `\n`     | Line Feed (`LF`)                      |
| Tab Size          | `4`      | Use Spaces                            |
| Tab Size          | `2`      | `*.{html,css,less,json,jsonc,yml,md}` |
| Semicolon         | `insert` |                                       |
| Quote Style       | `double` |                                       |
| Print Width       | `120`    | Except `*.md`                         |
| Trailing Comma    | `none`   |                                       |
| Arrow Parens      | `always` |                                       |

> _The shared Prettier configuration is part of our Custom Visual Templates._

## **ESLint**

[ESLint](https://eslint.org/ "Open") is the static code analyzer used throughout our projects. Through the shared `@falkor/falkor-eslint-config` NPM workspace, the rules (and versions) are handled independently, and can be extended on will inside descendant configurations.

> _The shared ESLint configuration is part of our Custom Visual Templates._

### **Abstract**

- ESLint is a static code analyzer.
  - Static code analysis is a method of computer program debugging that is done by examining the code without executing the program. The process provides an understanding of the code structure and can help ensure that the code adheres to industry standards.
  - ESLint is a tool for identifying and reporting on patterns found in ECMAScript/JavaScript code, with the goal of making code more consistent and avoiding bugs.
- ESLint is completely pluggable.
  - Every single rule is a plugin and you can add more at runtime.
  - We can utilize the 3rd party TypeScript ESLint plugin to lint our codebase:
    - Enables ESLint to parse and understand TypeScript syntax.
    - Alters ESLint rules to be able to use type information.
    - Provides rules that are specific to TypeScript and/or use type information.
- ESLint integrates in the IDE, but can be set up as project dependency.
  - Can use lightweight IDE with no ESLint integration.
  - Can be run separately from shell:
    - As packaging hook (early fail)
    - As version control hook (automated code review workflow)

### **Recommended Plugins**

- [TypeScript Plugin](https://typescript-eslint.io/ "Open")
- [Import Plugin](https://github.com/import-js/eslint-plugin-import "Open")
- [JSDoc Plugin](https://github.com/gajus/eslint-plugin-jsdoc "Open")
- [TypeScript Import Resolver](https://github.com/import-js/eslint-import-resolver-typescript "Open")
- [ESLint Disable Comments Plugin](https://mysticatea.github.io/eslint-plugin-eslint-comments/ "Open")
- [Prettier Config](https://github.com/prettier/eslint-config-prettier "Open")

## **CSpell**

[CSpell](https://cspell.org/ "Open") is the code spell checker used throughout our projects. Through the shared `@falkor/falkor-cspell-config` NPM workspace, the rules (and versions) are handled independently, and can be extended on will inside descendant configurations.

> _The shared CSpell configuration is part of our Custom Visual Templates._

### **Abstract**

- CSpell checks code for spelling issues.
  - Misspelled references can easily sneak their way deep into the codebase with IntelliSense.
- CSpell integrates in the IDE, but can be set up as project dependency.
  - Can use lightweight IDE with no CSpell integration.
  - Can be run separately from shell:
    - As packaging hook (early fail)
    - As version control hook (automated code review workflow)

## **Other Tools**

`// TODO`

##

---

_©2020-2023 Barnabas Bucsy - All rights reserved._
