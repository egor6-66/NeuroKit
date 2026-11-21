---
name: validate-external-data-on-entry
description: Validate parsed input against the expected Python model when loading external data, then pass the validated value to consumers.
---

At the point where a file, API response, or message enters the application, use the project’s existing model or validator to check its structure. A successful parse establishes that the syntax is readable. Type annotations and `typing.cast()` supply information to the type checker only. Return the validated value so downstream code can use its fields directly.

For example, suppose the project already defines a Pydantic `Recipe` model with a `seeds: list[str]` field. The YAML loader can use it directly:

```python
def load_recipe(text: str) -> Recipe:
    raw = yaml.safe_load(text)
    return Recipe.model_validate(raw)
```

Both `seeds: [review]` and `seeds: review` are valid YAML. The first should produce a recipe containing one seed. The second should report a validation error for `seeds` during loading. Passing the raw string onwards could cause a consumer to iterate over the letters in `review`. When reporting a load failure, keep the source (such as the file path) and the field error available.

[Python documentation on cast](https://docs.python.org/3.13/library/typing.html#typing.cast) · [Pydantic model validation](https://docs.pydantic.dev/latest/concepts/models/#validating-data)
