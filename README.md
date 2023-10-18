# NextJS-Zustand-Monorepo

NextJS-Zustand-Monorepo is a frontend component for 
[`compose-stack`](https://github.com/compose-stack/compose-stack).

It includes the following packages:

- [`Next.js`](https://nextjs.org/): the React framework for the Web
- [`Zustand`](https://github.com/pmndrs/zustand) as state manager
- [`Zod`](https://zod.dev/) for schema validation
- [`react-hook-form`](https://react-hook-form.com/) to build extensible forms

Additionally, it comes with built-in features:

- App based on Next.js's `app router`, with home page, user registration, logged in page, and user
  password reset form
- Users registration, verification, authentication and password reset
- Feature flags setup (one available, to control if new users can register or not)
- Monorepo structure based on [`yarn workspaces`](https://yarnpkg.com/features/workspaces);
- A documentation package based on Storybook (to be done)

The out-of-the-box setup allows to prototype applications that requires users
registration quickly.

#### Note: this frontend component requires a backend.

## TL;DR

Development:

```sh
cd frontend
yarn
yarn webapp:dev
```

Test:

```sh
cd frontend
yarn
yarn webapp:test
```


## Installation

Requirements:

- `docker` for the dockerized version, otherwise native installation is available.

### Native Installation & Run

```sh
cd frontend
yarn
yarn webapp:dev
```

The application will be available at: [`http://localhost:3000`](http://localhost:3000)

Due to slowness of the dockerized solution, running the package natively is
strongly advised.

## Build & Run with Docker

### First run

To build and run the frontend with Docker, first we need to build the image, 
then we can start the server.

```sh
docker compose -f docker-compose.dev.yml build
docker compose -f docker-compose.dev.yml up
```

This will run also a watcher for the `packages/ui` shared component library.

### Tests (great for TDD)

```sh
# run once or whenever a dependency change
docker compose -f docker-compose.test.yml build
# run the tests
docker compose -f docker-compose.test.yml up --exit-code-from cs-nextjs-zustand-monorepo-test
```

## TODO

- Use cookies for authentication
- Move client only components to a different package, so SSR can be used for almost all pages
- Create the `todos` branch and add Projects and Todos UI
- Add Storybook to document `packages/ui` components
