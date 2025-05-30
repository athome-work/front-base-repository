# Code basics

---

## Dependencies

Use package manager <kbd>pnpm</kbd>

**Install pnpm**

```sh
npm install -g pnpm
```

**Install new libraries with pnpm**

```sh
pnpm i angular --save-exact
```

## Folder structure

```
src/
├── app/
│   ├── core/
│   │   ├── services/
│   │   ├── interceptors/
│   │   ├── guards/
│   ├── shared/
│   │   ├── components/
│   │   ├── pipes/
│   │   ├── directives/
│   │   ├── interfaces/
│   ├── features/
│   │   ├── auth/
│   │   │   │── layouts/
│   │   │   │   │── main-layout/
│   │   │   │   │   ├── auth-layout.component.ts
│   │   │   │   │   └── auth-layout.component.html
│   │   │   ├── pages/
│   │   │   │   │── login/
│   │   │   │   │   ├── login.component.ts
│   │   │   │   │   └── login.component.html
│   │   │   ├── components/
│   │   │   ├── auth.routes.ts
│   │   │   └── auth.config.ts
│   │   ├── dashboard/
│   │   │   ├── dashboard.component.ts
│   │   │   ├── dashboard.routes.ts
│   │   │   └── dashboard.config.ts
│   │   └── ...
│   ├── app.routes.ts
├── assets/
├── environments/
└── main.ts
```

- No deben haber dependencias cruzadas entre módulos de <kbd>features/</kbd>.

- <kbd>shared/</kbd> está reservado únicamente para recursos reutilizables sin lógica de negocio.

- Cada módulo bajo <kbd>features/</kbd> debe incluir:

```
├── layouts/        # Componentes estructurales del módulo
├── pages/          # Componentes de página (ruteables)
├── components/     # Componentes reutilizables internos del módulo
├── auth.routes.ts  # Definición de rutas
└── auth.config.ts  # Configuración del módulo
```

- Se debe utilizar el CLI de angular para la creación de nuevos archivos

- Nunca incluir datos sensibles hardcoded en el frontend (API keys, tokens, etc) manejar este tipo de información dentro de los archivos environments.

- Usar Guards en rutas protegidas

- Centralizar textos en archivos i18n si se usa soporte multilenguaje.

- Evitar hardcoded strings en plantillas HTML.

- Usar async pipe en lugar de subscribe en plantillas.

- Prohibido el uso de any.

- Mantener los imports organizados.

- Aplicar principios SOLID en servicios y lógica de negocio.

- Usar lazy loading (loadChildren) para cada feature.

- Usar <kbd>PascalCase</kbd> a menos que sean siglas de 3 o menos carácteres, en ese caso se escribiria todo en mayúscula ej: <kbd>IP</kbd>, <kbd>ID</kbd>, <kbd>TLS</kbd>

---

## Variable and Function

- Use camelCase for variable and function names

**Bad**

```ts
var FooVar;
function BarFunc() {}
```

**Good**

```ts
var fooVar;
function barFunc() {}
```

---

## Class

- Use <kbd>PascalCase</kbd> for class names.

> **Reason:** Naturally follows from variable and function naming convention.

**Bad**

```ts
class Foo {
  Bar: number;
  Baz() {}
}
```

**Good**

```ts
class Foo {
  bar: number;
  baz() {}
}
```

---

## Interface

- Use <kbd>PascalCase</kbd>

- Use <kbd>camelCase</kbd> for members.

- Prefix with <kbd>I</kbd>

**Bad**

```ts
interface User {
  Name: string;
}
```

**Good**

```ts
interface IUser {
  name: string;
}
```

## Enums

- Use <kbd>PascalCase</kbd>

- Use <kbd>MAYUS</kbd> & <kbd>SNAKE_CASE</kbd> for members.

**Bad**

```ts
enum roles {
  admin = 1,
  alient = 2,
}
```

**Good**

```ts
enum ERoles {
  Admin = 1,
  Client = 2,
}
```

## Constants

**Bad**

```ts
const MessageTypes = [("TEXT" = 1), ("AUDIO" = 2), ("ATTACHMENTS" = 3), ("INTERACTIONS" = 4)];
```

**Good**

```ts
const DIAL_CODE_LENGTH = [
  "CO": 10
]

const MESSAGE_TYPES: {
  Text: 1;
  Audio: 2;
  File: 3;
  Interactions: 4;
};
```

## Null vs. Undefined

En el archivo <kbd>tsconfig.json</kbd> se deben agregar estas 2 lineas

```ts
"strictPropertyInitialization": false,
"strictNullChecks": false,
```

las declaraciones dentro de los componentes no es necesario inicializarlas siempre y cuando sean asignadas en algun momento del ciclo de vida del componente y los observables se deberan inizializar en null
