# ESPHome components

Custom ESPHome components maintained by [yaleman](https://github.com/yaleman).

## Components

### `esp32_ble_server`

Provides an ESP-IDF Bluetooth Low Energy GATT server with configurable
services, characteristics, descriptors, notifications, connection events, and
pairing events.

Load it from GitHub with ESPHome's `external_components` integration:

```yaml
external_components:
  - source: github://yaleman/esphome-components@main
    components:
      - esp32_ble_server
```

The component requires an ESP32 using the ESP-IDF framework. Configure the
Bluetooth transport separately with `esp32_ble` before adding an
`esp32_ble_server` block.

## Validation

[mise](https://mise.jdx.dev/) installs `uv`, and `uvx` runs the pinned ESPHome
release in an isolated environment:

```sh
mise install
uvx --from esphome==2026.7.4 esphome compile tests/esp32_ble_server.yaml
```

GitHub Actions runs the same compile for pushes and pull requests.
