---
name: use-framework-api
description: Build application features with the documented public APIs of web-core.
---

Before implementing a component, route, request, or other framework-level behavior, find the relevant web-core package. Read its README and the example closest to the task, using documentation for the version available to the app. For UI work, also read the component's own README. Check which behavior the framework supplies and which parts the application is expected to compose.

Use the public import paths documented by web-core. Bring third-party capabilities into applications through web-core. For example, use @web-core/query for requests so providers and consumers share the same query context. When building a creation form in a dialog, compose the form with the documented dialog parts and reuse their focus and dismissal behavior.

If the documented API appears insufficient, check its supported composition options and public exports. Identify the exact missing capability and agree on a web-core extension with the user before adding a workaround or dependency to the application.
