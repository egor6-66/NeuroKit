---
name: use-library-capabilities
description: Use supported library features for common mechanisms and keep project policy in the calling code.
---

Before implementing a common mechanism such as request handling, error handling, retries, or caching, check the standard library, the framework, and the project's existing dependencies. If none meets the requirement, evaluate a suitable library and the cost of adding it before building a custom implementation.
For a selected library, check the behavior, configuration, and extension points available in the version the project uses. Delegate supported operations to the library. Keep project policy and genuinely missing behavior in a wrapper when needed. Identify the specific unmet requirement before implementing custom behavior.
Give each operation one owner. For example, configure the HTTP client's retry conditions and attempt limit for a service. Let the client perform the attempts. An additional retry loop around that call can multiply requests when both layers retry.
