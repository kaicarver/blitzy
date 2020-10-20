# Blitzy

This is me trying out the Blitz.js tutorial.

## Notes

### (Minor) problems doing the tutorial

#### No anonymous default export

Can't commit the "simplest page possible in Blitz" without `--no-verify`.

<https://blitzjs.com/docs/tutorial#write-your-first-page>

because it gives a linting error:

<https://github.com/benmosher/eslint-plugin-import/blob/v2.22.1/docs/rules/no-anonymous-default-export.md>

I used the workaround

```typescript
/* eslint import/no-anonymous-default-export: [2, {"allowArrowFunction": true}] */
```

but it would be better to just do what lint recommends...

#### Jest not installed

Can't push to Github without `--no-verify`.

I get this unfriendly error:

```text
husky > pre-push (node v12.13.1)

> blitzy@1.0.0 lint /home/kai/blitzy
> eslint --ignore-path .gitignore --ext .js,.ts,.tsx .


> blitzy@1.0.0 test /home/kai/blitzy
> jest

No tests found, exiting with code 1
Run with `--passWithNoTests` to exit with code 0
No files found in /home/kai/blitzy.
Make sure Jest's configuration does not exclude this directory.
To set up Jest, make sure a package.json file exists.
Jest Documentation: facebook.github.io/jest/docs/configuration.html
Pattern:  - 0 matches
npm ERR! code ELIFECYCLE
npm ERR! errno 1
npm ERR! blitzy@1.0.0 test: `jest`
npm ERR! Exit status 1
npm ERR!
npm ERR! Failed at the blitzy@1.0.0 test script.
npm ERR! This is probably not a problem with npm. There is likely additional logging output above.

npm ERR! A complete log of this run can be found in:
npm ERR!     /home/kai/.npm/_logs/2020-10-20T10_22_34_907Z-debug.log
husky > pre-push hook failed (add --no-verify to bypass)
error: failed to push some refs to 'https://github.com/kaicarver/blitzy.git'
```

I'll try installing Jest to see if it goes away.

Update: no, Blitz comes with Jest installed already.

The important message is probably:

```text
No tests found, exiting with code 1
```

So probably I just need to add some test.
Why doesn't `blitz new` provide a test file so this won't happen?

#### Slow

Playing around with the app, first load of any page is very slow. Guess that's normal, maybe mostly noticeable in dev version?

#### Restart required

Changes here:

<https://blitzjs.com/docs/tutorial#writing-a-minimal-form>

required Ctrl-C and start before taking effect.

#### Compilation error

...

#### typo

Towards the end, 

```typescript
const updated = await updateChoice({
```

should be

```typescript
const updated = await updateChoiceMutation({
```







---

This is the boilerplate Blitz.js Readme.md:

[![Blitz.js](https://raw.githubusercontent.com/blitz-js/art/master/github-cover-photo.png)](https://blitzjs.com)

This is a [Blitz.js](https://github.com/blitz-js/blitz) app.

## Getting Started

Run your app in the development mode.

```
blitz start
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

## Environment Variables

Ensure the `.env.local` file has required environment variables:

```
DATABASE_URL=postgresql://<YOUR_DB_USERNAME>@localhost:5432/blitzy
```

Ensure the `.env.test.local` file has required environment variables:

```
DATABASE_URL=postgresql://<YOUR_DB_USERNAME>@localhost:5432/blitzy_test
```

## Tests

Runs your tests using Jest.

```
blitz test
or
yarn test
```

Blitz comes with a test setup using [Jest](https://jestjs.io/) and [react-testing-library](https://testing-library.com/).

## Commands

Blitz comes with a powerful CLI that is designed to make development easy and fast. You can install it with `npm i -g blitz`

```
  blitz [COMMAND]

  build     Create a production build
  console   Run the Blitz console REPL
  db        Run database commands
  generate  Generate new files for your Blitz project
  help      display help for blitz
  start     Start a development server
  test      Run project tests
```

You can read more about it on the [CLI Overview](https://blitzjs.com/docs/cli-overview) documentation.

## What's included?

Here is the structure of your app.

```
blitzy
├── app
│   |── auth
│   │   ├── components
│   │   │   └── LoginForm.tsx
│   │   ├── mutations
│   │   │   ├── login.ts
│   │   │   ├── logout.ts
│   │   │   └── signup.ts
│   │   └── pages
│   │       ├── login.tsx
│   │       └── signup.tsx
│   ├── auth-utils.ts
│   ├── validations.ts
│   ├── components
│   │   ├── Form.tsx
│   │   └── LabeledTextField.tsx
│   ├── hooks
│   │   └── useCurrentUser.ts
│   ├── layouts
│   │   └── Layout.tsx
│   │── pages
│   │   ├── _app.tsx
│   │   ├── _document.tsx
│   │   ├── 404.tsx
│   │   ├── index.tsx
│   │   └── index.test.tsx
│   └── users
│   │   └── queries
│   │       └── getCurrentUser.ts
├── db
│   ├── migrations
│   ├── index.ts
│   └── schema.prisma
├── integrations
├── node_modules
├── public
│   ├── favicon.ico
│   └── logo.png
├── test
│   ├── __mocks__
│   │       └── fileMock.js
│   ├── setup.ts
│   └── utils.tsx
├── utils
├── .env
├── .eslintrc.js
├── .gitignore
├── .npmrc
├── .prettierignore
├── babel.config.js
├── blitz.config.js
├── jest.config.js
├── package.json
├── README.md
├── tsconfig.json
└── yarn.lock
```

These files are:

- The `app/` directory is a container for most of your project. This is where you’ll put any pages or API routes.

- `db`/ is where your database configuration goes. If you’re writing models or checking migrations, this is where to go.

- `node_modules/` is where your “dependencies” are stored. This directory is updated by your package manager, so you don’t have to worry too much about it.

- `public/` is a directory where you will put any static assets. If you have images, files, or videos which you want to use in your app, this is where to put them.

- `test/` is a directory where you can put your unit and integration tests.

- `utils/` is a good place to put any shared utility files which you might use across different sections of your app.

- `.babelrc.js`, `.env`, etc. ("dotfiles") are configuration files for various bits of JavaScript tooling.

- `blitz.config.js` is for advanced custom configuration of Blitz. It extends [`next.config.js`](https://nextjs.org/docs/api-reference/next.config.js/introduction).

- `jest.config.js` contains config for Jest tests. You can [customize it if needed](https://jestjs.io/docs/en/configuration).

- `package.json` contains information about your dependencies and devDependencies. If you’re using a tool like `npm` or `yarn`, you won’t have to worry about this much.

- `tsconfig.json` is our recommended setup for TypeScript.

You can read more about it in the [File Structure](https://blitzjs.com/docs/file-structure) section of the documentation.

## Learn more

Read the [Blitz.js Documentation](https://blitzjs.com/docs/getting-started) to learn more.

### The Blitz.js Manifesto

Read the [Blitz Manifesto](https://blitzjs.com/docs/manifesto) to learn the Blitz foundational principles.

Blitz is built on Next.js. For more info on this see [Why use Blitz instead of Next.js](https://blitzjs.com/docs/why-blitz)

## Get in touch

The Blitz community is warm, safe, diverse, inclusive, and fun! Feel free to reach out to us in any of our communication channels.

- [Website](https://blitzjs.com/)
- [Slack](https://slack.blitzjs.com/)
- [Report an issue](https://github.com/blitz-js/blitz/issues/new/choose)
- [Forum discussions](https://github.com/blitz-js/blitz/discussions)
- [Sponsors and donations](https://github.com/blitz-js/blitz#sponsors-and-donations)
- [Contributing Guide](https://blitzjs.com/docs/contributing)
