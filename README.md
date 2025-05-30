# Frontend-base-repository

## Start commands

Create a new project using nvm and specific version of Angular

- Select node version to use

```bash
nvm select 24.0.1
```

- Run Angular CLI creation command with npx to use previusly node selected version

```bash
npx ng new frontend-base-repository --package-manager=pnpm
```

- In this case add Docsify for the documentation

```bash
pnpm i -DE docsify-cli
```

- Add documentations run command in <kbd>package.json</kbd>

```json
{
    ...
    "scripts": {
        ...
        "docs": "docsify serve ./docs"
    }
    ...
}
```

- Add **prettier**

```bash
pnpm i -DE prettier
```

- Add **Eslint**

```sh
ng add @angular-eslint/schematics
pnpm install @eslint/js @eslint/eslintrc -DE
pnpm install @typescript-eslint/eslint-plugin@latest -DE
pnpm install @angular-eslint/eslint-plugin@latest -DE
pnpm install @angular-eslint/eslint-plugin-template@latest -DE
```

- Create <kbd>.prettierrc</kbd> in root folder

```json
{
  "printWidth": 120,
  "singleQuote": false,
  "trailingComma": "all",
  "bracketLine": false,
  "proseWrap": "preserve",
  "htmlWhitespaceSensitivity": "css",
  "endOfLine": "lf",
  "singleAttributePerLine": false,
  "eslintIntegration": true
}
```

- Install ESLint & Prettier extension plugins in visual studio code

- Active **Format on save** & **Fefault formater: prettier**

```json
{
  ...
  "editor.rulers": [
    100,
    120
  ],
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
}
```

- Install and init **lint-stages**

```bash
pnpm i -DE lint-staged
```

- Create <kbd>.lintstagedrc.json</kbd>

```json
{
  "*.ts": ["eslint --fix", "prettier --write"],
  "*.html": ["prettier --write", "eslint --fix"],
  "*.scss": ["prettier --write"]
}
```

- Install and init **huskey**

```bash
pnpm add -DE husky
pnpm exec husky init
```

- Modify <kbd>.husky/pre-commit</kbd>

```bash
pnpm dlx lint-staged
```

- Add PrimeNG

```bash
pnpm add primeng @primeng/themes
```

- Add tailwind

```bash
pnpm i -E tailwindcss-primeui
```

- Import tailwind

```ts
@import "tailwindcss";
@plugin "tailwindcss-primeui";
```

- Install Storybook

```bash
pnpm install -DE @types/node
pnpm dlx storybook@latest init
```
