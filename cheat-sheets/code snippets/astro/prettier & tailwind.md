### Adding Tailwind CSS and Prettier

With our [Astro](https://astro.build/) project set up, it's time to add [Tailwind CSS](https://tailwindcss.com/) and [Prettier](https://prettier.io/). Run the following commands from within your new [Astro project folder](https://docs.astro.build/en/core-concepts/project-structure/) and accept the default options when prompted:

```
pnpm dlx astro add tailwindcss
pnpm add -D prettier prettier-plugin-astro prettier-plugin-tailwindcss
```
### Configuring Prettier

To [configure Prettier](https://prettier.io/docs/en/options.html), create a `.prettierrc` file in the root directory of your project and paste the following configuration:
```
{
   "useTabs": true,
   "singleQuote": true,
   "trailingComma": "none",
   "semi": false,
   "printWidth": 100,
   "plugins": ["prettier-plugin-astro", "prettier-plugin-tailwindcss"],
   "pluginSearchDirs": false
}
```

It's essential to include the `plugins` and `pluginSearchDirs` properties in this context; otherwise, the integration will not function as intended. When working with a framework integration, such as [Svelte](https://svelte.dev/) (`prettier-plugin-svelte`), it's necessary to include them in the `plugins` properties.

Additionally, create a `.prettierignore` file with the following content to exclude specific files from [Prettier's formatting](https://prettier.io/docs/en/index.html):
```
node_modules/**
```