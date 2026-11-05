# UI Framework Switching

This repository includes a frontend application based on `Antdv Next`. To use another component library, add an application under `apps` and adapt its forms, components, and theme as needed.

## Adding a New UI Framework

If you want to use a different UI framework, you only need to follow these steps:

1. Create a new folder inside `apps`, for example, `apps/web-xxx`.
2. Change the `name` field in `apps/web-xxx/package.json` to `web-xxx`.
3. Remove dependencies and code from other UI frameworks and replace them with your chosen UI framework's logic, which requires minimal changes.
4. Adjust the language files within `locales`.
5. Adjust the components in `app.vue`.
6. Adapt the theme of the UI framework to match `Vben Admin`.
7. Adjust the application name in `.env`.
8. Add a `dev:xxx` script in the root directory of the repository.
9. Run `pnpm install` to install dependencies.
