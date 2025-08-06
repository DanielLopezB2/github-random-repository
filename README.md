# Github Random Repository
Create a GitHub random repository finder using GitHub API. From https://roadmap.sh/projects/github-random-repo

- Will create a GitHub repository finder that allows users to select a programming language from a dropdown menu. The app will then use the GitHub Repository Search API to fetch and display a random repository that matches the selected language. The displayed information should include the repository name, description, number of stars, forks, and open issues. Users can fetch another random repository with a button click.

- The application should handle loading, empty, and error states effectively. After successfully fetching a repository, a “Refresh” button should appear to allow users to get another random repository.

Here are the links to the resources will need for this project:

GitHub Repository Search API -> https://docs.github.com/en/rest/search/search?apiVersion=2022-11-28#search-repositories
Programming Language Data -> https://raw.githubusercontent.com/kamranahmedse/githunt/master/src/components/filters/language-filter/languages.json

This project will help practice API integration, managing asynchronous data, and enhancing user experience with responsive UI states.


## Setup

Make sure to install dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm dev

# yarn
yarn dev

# bun
bun run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.
