# next-mini18n
## A minimal, type-safe internationalization library

### Goals
* Minimal wire transfer: Don't send all translations on each page load.
* Modular: Add only the functionality you need.
* Type-Safety: Use typescript for code completion when accessing translations
and refactor with ease.
* Bundle size: Keep the client side bundle small.
* Framework integration: This is built for nextjs
* Minimalism: Keep the API surface small.

### Non-goals
* Batteries included: This library is not intended to do much on its own.
* Other Frameworks: This is meant for react and nextjs.
* Cleverness: This is supposed to stay simple and predictable.

## Usage
* Define translations in separate files next to your components:
```ts
// i18n/en.ts
const en = {
    Hello: 'Hello',
    World: 'World',
}
export default en
```

* Lazy-load the translation files
```ts
// pages/index.tsx
import mini18n from "next-mini18n"

const { Hello, World } = mini18n((locale) => import(`i18n/${locale}`))
```

* Use them in your component:
```ts
export default function HomePage() {
    return <h3><Hello /> <World /></h3>
}
```
## What's cool about this?
* It uses next/dynamic under the hood and therefore causes no trouble with SSR.
* It needs very little client side code
* You get nice completions when writing components
* You get type errors when removing or renaming translations that are used somewhere
* Interpolations are just functions
* Translations can be arbitrary react components

## What's less cool about this
* It uses next/dynamic under the hood and therefore loads translations lazily _after_ the first render cycle.

## Examples
There's an example in the example-folder.