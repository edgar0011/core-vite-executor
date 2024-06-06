# @e1011/core-vite-executor

#### Core-vite-executor is utility lib for running CoreVite locally.

**Prerequisites**

- **nodejs** (>=18 <19)
- **npm**
- **yarn** (yarn exec) or **pnpm** (pnpm exec) can be used technically.

## Run CoreVite as Node binary
In order to be able to test micro UI (based on [vite-app-example](https://github.com/edgar0011/core-vite-app-example)), the user can trigger `core-vite` installation and build without the need to manually git clone, install, and run.

Pass the path to `routes.config.json` as argument and `core-vite` will run the micro UIs defined.

Example of minimal routes config:
```json
{
  "routes": {
    "basePath": "/app",
    "auth": {
      "vite-app-example": {
        "name": "core-vite-app-example",
        "icon": "applicationsIcon",
        "tooltipText": "core-vite-app-example",
        "apps": [
          {
            "cssFiles": "[\"http://localhost:2001/bundle.css\"]",
            "jsFiles": "[\"http://localhost:2001/bundle.js\",\"http://localhost:2001/bundle.umd.js\"]",
            "mountId": "ui-core-vite-app-example",
            "config": "{\"basePath\":\"/app/core-vite-app-example\"}",
            "loader": true,
            "data-sample-attribute": "some serialized data for core-vite-app-example"
          }
        ]
      }
    },
    "unauth": {}
  }
}

```

```sh
npx @e1011/core-vite-executor path/to/routes.config.minimal.json
```
**`path/to/routes.config.minimal.json` is optinal can be only directory, and core-vite-executor will try to find the routes config there. It also defaults to `./`.**

to make sure the latest version of the `core-vite-executor` is installed in the local npm repository, add `@latest`:
```sh
npx @e1011/core-vite-executor@latest path/to/
```

Every subsequent run (if no new version is available when using `@latest`) will run the already built `core-vite`. To rebuild it add 2nd (or 3rd) param `rebuild`.

`npx @e1011/core-vite-executor ./routes.config.minimal.json rebuild`
