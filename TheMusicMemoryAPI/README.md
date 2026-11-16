# React + TypeScript + Vite

## Base de données Prisma

La base SQLite est définie dans [`prisma/schema.prisma`](prisma/schema.prisma).
Elle contient :

- `User` : identifiant utilisateur, login, e-mail de récupération et mot de passe ;
- `ExternalAlbum` : uniquement l'identifiant d'album fourni par l'API externe ;
- `UserAlbum` : table d'association entre utilisateurs et albums, avec une note
  personnelle de 1 à 5.

`UserAlbum` utilise une clé primaire composite `(userId, albumId)` et ne possède
pas d'identifiant `id` artificiel. Les artistes, les morceaux séparés et leurs
métadonnées ne sont pas sauvegardés.

Commandes Prisma :

```bash
bun run db:generate
bun run db:migrate
```

This template provides a minimal setup to get React working in Vite with HMR and some Oxlint rules.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Oxc](https://oxc.rs)
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/)

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the Oxlint configuration

If you are developing a production application, we recommend enabling type-aware lint rules by installing `oxlint-tsgolint` and editing `.oxlintrc.json`:

```json
{
  "$schema": "./node_modules/oxlint/configuration_schema.json",
  "plugins": ["react", "typescript", "oxc"],
  "options": {
    "typeAware": true
  },
  "rules": {
    "react/rules-of-hooks": "error",
    "react/only-export-components": ["warn", { "allowConstantExport": true }]
  }
}
```

See the [Oxlint rules documentation](https://oxc.rs/docs/guide/usage/linter/rules) for the full list of rules and categories.
