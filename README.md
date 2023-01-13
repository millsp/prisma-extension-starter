# Prisma Extension Starter

This package is a template to get ready and publish a Client Extension.

## Dependencies

For good practices, published extensions should not directly depend on the
Prisma Client. Instead, `@prisma/client` should be a peer dependency. Because of
this, it is recommended to use the `^` in your peer dependency version.

> 💡 Please be aware that Prisma Client Extensions are in preview, this means we
> can ship breaking changes without respecting versioning until the feature is
> generally available.

## Compilation

The `npm run build` script is used to compile the extension and outputs the `js`
contents into the `dist` folder. It will emit both `js` and `ts`.

## Code

The extension code should be written in the `src` folder in the `index.ts` file.
An extension must be exported and be defined with `Prisma.defineExtension`.

In generated clients, `Prisma.defineExtension` has rich auto-complete support.
Here, we are in a non-generated context, and auto-completions are best-effort.

Also, you should not import the generated client directly. Instead, you will
need to depend on the stub Prisma Client files for non-generated clients.

```ts
import { Prisma } from '@prisma/client/scripts/default-index'
```

## Example

```ts
import { Prisma } from '@prisma/client/scripts/default-index'

export const simpleExtension = Prisma.defineExtension({
  model: {
    $allModels: {
      simpleCall<T, A>(this: T, args: Prisma.Exact<A, Prisma.Args<T, 'findFirst'>>) {
        return {} as Prisma.Result<T, A, 'findFirst'>
      }
    }
  }
})
```