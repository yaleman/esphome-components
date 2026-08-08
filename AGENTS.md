# Repository Guidelines

## Structure

Custom integrations live under `components/<component_name>/`. Keep one
compile fixture per component under `tests/`, named `<component_name>.yaml`.
GitHub Actions workflows live under `.github/workflows/`.

Update `README.md` and this file when contributors or automation need to know
about a new workflow, component requirement, or repository convention.

## Dependencies and validation

Use `mise` to install command-line tools and `uv` or `uvx` to run Python tools.
Do not install ESPHome globally or maintain a hand-written virtual environment.
ESPHome is pinned in validation commands so local and CI results use the same
release.

After changing a component or its fixture, run:

```sh
mise install
uvx --from esphome==2026.7.4 esphome compile tests/esp32_ble_server.yaml
```

Add every component fixture to `.github/workflows/test.yaml` so pull requests
compile all supported components.

## Component conventions

Keep configuration validation in Python and runtime behavior in the
component's C++ sources. Report invalid configurations with ESPHome validation
errors. Handle runtime failures explicitly and log diagnostics at an
appropriate level. Do not commit `.esphome/`, `__pycache__/`, firmware build
output, credentials, or device-specific secrets.

In documentation and comments, use project-relative paths rather than absolute
paths.
