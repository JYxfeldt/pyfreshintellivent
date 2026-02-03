# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with this repository.

## Project Overview

pyfreshintellivent is a Python library for controlling Fresh Intellivent Sky bathroom ventilation fans via Bluetooth Low Energy (BLE). It provides an async interface to read sensor data and configure fan modes.

## Development Commands

```bash
# Install dependencies
poetry install

# Run tests
poetry run pytest

# Run linting
poetry run black .
poetry run flake8
poetry run isort .

# Check poetry configuration
poetry check
```

## Architecture

- **`pyfreshintellivent/__init__.py`**: Main `FreshIntelliVent` class - handles BLE connection, authentication, and mode operations
- **`pyfreshintellivent/parser.py`**: `SkyModeParser` - encodes/decodes BLE characteristic data for fan modes
- **`pyfreshintellivent/sensors.py`**: `SkySensors` - parses sensor data (temperature, humidity, RPM, light, VOC)
- **`pyfreshintellivent/characteristics.py`**: BLE GATT characteristic UUIDs
- **`pyfreshintellivent/helpers.py`**: Utility functions for byte/hex conversion and detection level mapping
- **`examples/`**: Usage examples for device discovery and reading data

## Fan Modes

The library supports these operational modes:
- **Humidity**: Auto-ventilation based on humidity detection
- **Light & VOC**: Triggered by light or air quality sensors
- **Constant Speed**: Fixed RPM operation
- **Timer**: Timed operation with optional delay
- **Airing**: Periodic ventilation at set intervals
- **Pause**: Temporarily pause the fan
- **Boost**: High-speed burst for set duration

## Testing

Tests are in `tests/` using pytest-asyncio. Tests cover parser encoding/decoding for each mode without requiring actual BLE hardware.

## Code Style

- Formatting: black
- Linting: flake8
- Import sorting: isort (profile: black)
- Python 3.10+ required (supports 3.10, 3.11, 3.12)
