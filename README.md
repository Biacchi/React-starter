# React-starter

My "hello React" playground: a Create React App project that runs inside Docker, so I never have to install Node on my machine to try something out. Currently it shows the default spinning logo with a few extra greeting lines I typed while checking that hot reload works. Very ambitious.

It is an early learning project and a handy template for starting new ones.

## Running it

With Docker (what I use):

```
docker-compose up --build
```

Then open http://localhost:3000. The compose file mounts the project folder into the container, and `WATCHPACK_POLLING=true` makes file changes reload properly even on Windows.

Without Docker (needs Node installed; the Dockerfile uses Node 18):

```
npm install
npm start
```

Other scripts from `package.json`: `npm test`, `npm run build`.

## What is in here

```
src/                 App.js, index.js and the default CRA files, plus one App.test.js
public/              index.html, icons, manifest
Dockerfile           node:18-alpine, npm install, npm start
docker-compose.yml   dev container with live reload on port 3000
```

## What I learned

- How a React app is bootstrapped and structured
- Putting a dev server in a container with a bind mount and polling
- The usual dance of keeping `node_modules` inside the container

## Known limitations

- This is the stock Create React App setup (`react-scripts` 5), which is no longer actively maintained. `npm audit` reports a pile of known issues in its dependency tree; they are in the dev tooling, but I have not upgraded anything (see the PR for the numbers).
- The Dockerfile only runs the dev server. There is no production build image.
- `src/App.test.js` is the default test and probably does not match the current text on the page.
- No LICENSE file yet, so by default all rights are reserved.

The original Create React App docs live at https://create-react-app.dev/.
