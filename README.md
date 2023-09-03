# UP CSI Website

The University of the Philippines Center for Student Innovations (UP CSI) website is a statically generated website built with the [SvelteKit] framework, which uses [Vite] as its build system under the hood. Components are then styled as [Flowbite] components using [TailwindCSS].

[SvelteKit]: https://kit.svelte.dev/
[Vite]: https://vitejs.dev/
[TailwindCSS]: https://tailwindcss.com/
[Flowbite]: https://flowbite.com/

# Development

We use [`pnpm`] as the package manager for [Node.js]. See the installation guide [here](https://pnpm.io/installation).

[`pnpm`]: https://pnpm.io/
[Node.js]: https://nodejs.org/

```bash
# Install the project dependencies.
pnpm install

# Same as the file watcher, but also starts a developer server at
# `localhost:5173` by default. Live-reloading and hot module replacement
# has been disabled by default.
pnpm dev

# Build and optimize the project. Static assets are saved to `build/`.
pnpm build

# Locally preview the production website after building.
pnpm preview
```

To maintain a high standard in the codebase, we use [GitHub Actions] to automatically run formatters (i.e., [Prettier]), linters (i.e., [HTMLHint], [Stylelint], [ESLint], and [Svelte Check]), and builders (i.e., [Parcel]) for each push to the repository (including pull requests). We strive to keep `main` at a green state (i.e., all tests pass) at all times. **No exceptions.**

[GitHub Actions]: https://github.com/features/actions
[Prettier]: https://prettier.io/
[HTMLHint]: https://htmlhint.com/
[Stylelint]: https://stylelint.io/
[ESLint]: https://eslint.org/
[Svelte Check]: https://www.npmjs.com/package/svelte-check

Before pushing to the repository, one may be inclined to locally run the formatters, linters, and builders themselves.

```bash
# Check the code formatting with Prettier.
pnpm fmt

# Apply Prettier's suggestions.
pnpm fmt:fix

# Run all linters: HTMLHint, Stylelint, ESLint, and Svelte Check.
pnpm lint
```

# Frequently Asked Questions

## How does one write new content?

Simply edit the HTML and Svelte components. Add Tailwind styles as deemed necessary. Pull requests are _highly_ encouraged.

## Why not use a content management system like WordPress?

Statically generating the website allows the build system to _aggressively_ prune unused code, optimize resources, and minify assets. Given that the end result is a single immutable `build/` folder that contains everything (e.g., HTML, CSS, JS, images, fonts, etc.), the website is thus _incredibly trivial_ to deploy and cache. Such a setup is practically the pinnacle of web performance. Many services will even host the static content for free! No need for a fancy server-side-rendered [Django] application nor a bloated [WordPress] instance powered by an [Apache] server running [PHP] code with [MySQL] as the backing content store.

[Django]: https://www.djangoproject.com/
[Wordpress]: https://wordpress.org/
[Apache]: https://apache.org/
[PHP]: https://www.php.net/
[MySQL]: https://www.mysql.com/

## Why do we use `pnpm` and not the default `npm`?

Unlike `npm`, `pnpm` is fast and space-efficient. Instead of downloading an entire tree of `node_modules` for _each_ project, `pnpm` globally stores all packages so that future installations simply symlink to the common folder. This alone empowers `pnpm` to [outperform](https://pnpm.io/benchmarks) all other package managers in the market. See more details in the [documentation](https://pnpm.io/motivation).

# Credits

-   This repository was originally bootstrapped by [Basti Ortiz](https://bastidood.github.io/) during the Academic Year 2023-2024 when he served as the UP CSI Director for Engineering.
    -   Repository Setup
    -   Automation with GitHub Actions
    -   Original Build System with Parcel
    -   New Build System with Vite
