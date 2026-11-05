# Slimmed-Down Version

Starting from version `5.0`, we no longer provide slimmed-down repositories or branches. Our goal is to offer a more consistent development experience while reducing maintenance costs. Here’s how we introduce our project, slim down, and remove unnecessary features.

## Application Slimming

This repository keeps `web-antdv-next` as its frontend application. When slimming down another project, remove the application directories you do not need and clean up their scripts and deployment configuration.

::: tip

If your project doesn’t include the `UI` component library you need, you can delete all other applications and create your own new application as needed.

:::

## Demo Code Slimming

If you don’t need demo code, you can simply delete the `playground` folder

## Documentation Slimming

If you don’t need documentation, you can delete the `docs` folder.

## Remove Mock Service

If you don’t need the `Mock` service, you can delete the `apps/backend-mock` folder. Also, remove the `VITE_NITRO_MOCK` variable from the `.env.development` file in your application.

```bash
# Whether to enable Nitro Mock service, true to enable, false to disable
VITE_NITRO_MOCK=false
```

## Installing Dependencies

Now that you’ve completed the slimming operations, you can install the dependencies and start your project:

```bash
# Run in the root directory
pnpm install

```

## Adjusting Commands

After slimming down, you may need to adjust commands according to your project. In the `package.json` file in the root directory, you can adjust the `scripts` field and remove any commands you don’t need.

```json
{
  "scripts": {
    "build:antdv-next": "pnpm run build --filter=@vben/web-antdv-next",
    "build:docs": "pnpm run build --filter=@vben/docs",
    "build:play": "pnpm run build --filter=@vben/playground",
    "dev:antdv-next": "pnpm -F @vben/web-antdv-next run dev",
    "dev:docs": "pnpm -F @vben/docs run dev",
    "dev:play": "pnpm -F @vben/playground run dev"
  }
}
```
