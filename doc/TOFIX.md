# TOFIX

Findings from a code scan on 2026-10-04.

## Low

- `rsconstruct.toml:21` - `ijsonlint` only checks JSON syntax; nothing validates `with_schema/foo.json` against the `$schema` it declares, so the one thing the `with_schema` demo is about is never exercised by the build. Add a schema-validating check (e.g. an explicit processor running `check-jsonschema` from the repo venv) so a value that violates the coffeelint schema fails the build.
- `with_schema/foo.json:2` - `$schema` uses `http://json.schemastore.org/coffeelint`, which answers with a 301 to https; use the canonical `https://json.schemastore.org/coffeelint.json` (the schema's own `$id`).
