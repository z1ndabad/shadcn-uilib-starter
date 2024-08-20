# shadcn-uilib-starter

## Intro
This is a minimal starter config for a UI library based on [shadcn-ui](https://ui.shadcn.com/) React components. It includes:
- [Tailwind](https://tailwindcss.com/) for styling
- [Storybook](https://storybook.js.org/docs) for component development.

## Structure
| File/s | Notes |
| ------------- | ------- |
| `src/index.ts` | Component exports only |
| `src/globals.css` | CSS variable definitions |
| `src/components/*/*.tsx` | Actual component files |
| `src/components/*/*.stories.tsx` | Storybook stories for development |
| `package.json` | Build scripts -- build:styles will use postcss-cli to combine CSS files |
| `postcss.config.js` | postcss plugin configuration, i.e. for postcss-import to combine CSS files |
| `tailwind.config.js` | Define entrypoints, plugins, global theme properties for Tailwind |
| `vite.config.ts` | Handles building package in `dist` using Vite in [library mode](https://vitejs.dev/guide/build#library-mode) |

## Usage
- Create your own lib from the template
- Add desired shadcn-ui components to `src/components/MyComponent`
- Modify styling. Some options are:
  - Editing component files directly, e.g. by editing variants
  - Editing global CSS variables defined in `src/globals.css`
  - Adding new CSS files for users to import (e.g. for multi-theme setups) in `src/themes`
  - Editing `tailwind.config.js` per the [docs](https://tailwindcss.com/docs/configuration)
- Publish + profit

## Local development
Storybook is set up for local development. Create a `*.stories.tsx` file for component and run `npm run storybook` to work on it in the UI.

To consume component libraries built with this starter before publishing to a registry, you can:
- Run `npm link` in your library's working directory
- Run `npm link [my-library-]` in the working directory of the consuming application
- Import my-library in the consuming app as normal

## Notes
- There is an example config for adding additional fonts (JetBrains Mono Variable), using @fontsource:
  - Font imported in `package.json` and attached to a new global variable `font-code` in `src/globals.css`
  - Tailwind utility class for `font-code` specified in `tailwind.config.js`
  - `src/components/Button/Button.tsx` applies the utility class
- Build will produce an error from postcss-cli if `src/themes` is empty -- the build still passes

## TODO
- Improve tree-shaking and minification
- Make the template more opinionated?
