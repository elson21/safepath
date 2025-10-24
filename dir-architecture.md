# Stalker Tracker - Directory Structure

## PlatformIO Project Architecture

```
stalker-tracker/
├── README.md
├── platformio.ini                 # PlatformIO configuration
├── include/
│   ├── config.h                   # Configuration constants (thresholds, pins, etc.)
│   ├── wifi_scanner.h             # WiFi scanning interface
│   ├── mac_tracker.h              # MAC address tracking logic
│   ├── alert_manager.h            # Alert handling (LED, future vibration)
│   └── utils.h                    # Helper functions (time, memory management)
├── src/
│   ├── main.cpp                   # Entry point, setup() and loop()
│   ├── wifi_scanner.cpp           # WiFi promiscuous mode implementation
│   ├── mac_tracker.cpp            # MAC tracking algorithm & sliding window
│   ├── alert_manager.cpp          # LED control and alert logic
│   └── utils.cpp                  # Utility implementations
├── lib/                           # External libraries (if any)
├── test/                          # Unit tests (optional for MVP)
└── docs/
    ├── hardware_setup.md          # Wiring diagrams, board selection
    └── algorithm_design.md        # Detection logic documentation
```

## Module Responsibilities

### `config.h`
- Detection thresholds (e.g., 5 occurrences)
- Time window (e.g., 15 minutes)
- Pin definitions (LED_PIN, etc.)
- Scan intervals and duty cycle settings

### `wifi_scanner.cpp/h`
- Initialize WiFi in promiscuous mode
- Capture 802.11 management frames
- Extract MAC addresses from probe requests
- Callback for new MAC detections

### `mac_tracker.cpp/h`
- Store MAC addresses with timestamps
- Implement sliding time window (15 min)
- Count occurrences per MAC
- Clean up expired entries
- Check if stalking threshold exceeded

### `alert_manager.cpp/h`
- Control LED state (on/off/blink patterns)
- Future: vibration motor control
- Future: Bluetooth notifications

### `utils.cpp/h`
- Time management functions
- Memory cleanup utilities
- Debug logging helpers

### `main.cpp`
- Initialize all modules
- Main event loop
- Coordinate between scanner → tracker → alert

## Data Flow

```
WiFi Scan → Extract MAC → Store in Tracker → Check Threshold → Trigger Alert
     ↓            ↓              ↓                 ↓              ↓
wifi_scanner  wifi_scanner  mac_tracker      mac_tracker   alert_manager
```

## PlatformIO Configuration

The `platformio.ini` will specify:
- Board: `esp32-c3-devkitm-1` (or your specific board)
- Framework: `arduino` or `espidf`
- Libraries: None needed for MVP (using ESP-IDF built-in WiFi)
- Monitor speed: 115200

## Future Expansion Points

- `lib/bluetooth/` - BLE communication module
- `lib/storage/` - SPIFFS/LittleFS for ignore list persistence
- `lib/power/` - Sleep mode and power optimization
- `lib/gsm/` - SMS alert module (bonus feature)