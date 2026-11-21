---
name: use-framework-api
description: Build application features with the documented public APIs of web-core.
---

Before implementing a component, route, request, or other framework-level behavior, find the relevant web-core package. Read its README and the example closest to the task, using documentation for the version available to the app. Check which behavior the framework supplies and which parts the application is expected to compose.

Use the public import paths documented by web-core. Bring third-party capabilities into applications through web-core.

If the documented API appears insufficient, check its supported composition options and public exports. Identify the exact missing capability and agree on a web-core extension with the user before adding a workaround or dependency to the application.
