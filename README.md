# Nest Audio Drop-In PCB Replacement

Open-source hardware replacement PCB for the Google Nest Audio smart speaker with Home Assistant integration.

## Overview

This project provides a drop-in replacement PCB for the Google Nest Audio, converting it into a fully open-source Home Assistant voice assistant. The design is inspired by the [nest-mini-drop-in-pcb](https://github.com/iMike78/nest-mini-drop-in-pcb) project and follows the Home Assistant Voice Preview Edition hardware specification.

## Features

- **ESP32-S3R8**: Dual-core WiFi & Bluetooth with wake-word detection
- **XMOS XU316**: DSP audio processing with AEC, noise suppression, and beamforming
- **High-power amplifier**: Upgraded for Nest Audio's larger speaker drivers
- **USB-C + 14V barrel power**: Flexible power input options
- **Drop-in replacement**: Fits original Nest Audio enclosure
- **Home Assistant compatible**: Native Voice Assistant support
- **Open source hardware**: CERN-OHL-S v2 licensed

## Hardware Specifications

### PCB Dimensions
- **Length**: [TBD - from your scan]
- **Width**: [TBD - from your scan]
- **Thickness**: 1.6mm (standard)
- **Mounting**: Compatible with original T6 screw holes

### Components
| Component | Model | Purpose |
|-----------|-------|---------|
| MCU | ESP32-S3R8 | WiFi, BLE, wake-word |
| DSP | XMOS XU316-1024-QF60B | Audio processing |
| Amplifier | [TBD - higher power than mini] | Speaker driver |
| Microphones | Dual MEMS | Far-field voice capture |
| LEDs | [TBD] | Status indication |
| Power | USB-C + 14V barrel | Power input |

### Audio Chain
1. Dual MEMS microphones → XMOS DSP (AEC, beamforming)
2. XMOS → ESP32-S3 (I2S)
3. ESP32-S3 → WiFi → Home Assistant
4. Home Assistant response → ESP32-S3 → Amplifier → Speaker

## Getting Started

### 1. Order PCB
- Download KiCad files from `hardware/kicad/`
- Upload to PCB manufacturer (JLCPCB, PCBWay, etc.)
- Recommended: 1.6mm thickness, ENIG finish

### 2. Order Components
- See `hardware/bom/bill-of-materials.csv`
- Available from Digi-Key, Mouser, LCSC

### 3. Assemble
- Follow `docs/assembly-guide.md`
- Requires hot air station for QFN packages
- Test points provided for debugging

### 4. Flash Firmware
- Follow `docs/flashing-guide.md`
- Uses ESPHome configuration
- OTA updates supported

### 5. Install
- Remove original Nest Audio PCB
- Install this PCB using original mounting screws
- Connect speakers and power

## Documentation

- [Assembly Guide](docs/assembly-guide.md)
- [Flashing Guide](docs/flashing-guide.md)
- [Measurements](docs/measurements.md)
- [Troubleshooting](docs/troubleshooting.md)

## Hardware Design

### KiCad Project
- Open `hardware/kicad/nest-audio-pcb.kicad_pro` in KiCad 9.0+
- Schematics in `hardware/kicad/*.kicad_sch`
- PCB layout in `hardware/kicad/*.kicad_pcb`

### Key Design Files
- `audio.kicad_sch` - Audio processing and amplification
- `power.kicad_sch` - Power management and regulation
- `mcu.kicad_sch` - ESP32-S3 and XMOS connections
- `io.kicad_sch` - Connectors and interfaces

## Firmware

### ESPHome Configuration
```yaml
# See firmware/esphome/nest-audio.yaml
esp32:
  board: esp32-s3-devkitc-1
  variant: esp32s3
  flash_size: 8MB
  
# Home Assistant Voice Assistant
voice_assistant:
  microphone: mic_array
  speaker: amp_output
```

### Features
- Wake word detection ("Hey Jarvis", "OK Google", custom)
- Local voice processing with Wyoming protocol
- OTA firmware updates
- WiFi provisioning via BLE
- Status LED control
- Volume control

## Project Status

- [x] Project initialization
- [ ] Hardware measurements from 3D scan
- [ ] KiCad schematic design
- [ ] PCB layout and routing
- [ ] Prototype testing
- [ ] Documentation complete
- [ ] First release

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### Areas needing help:
- PCB measurements and verification
- Audio amplifier selection for larger drivers
- Thermal management testing
- Enclosure modifications guide
- Firmware optimizations

## Credits

- **Inspired by**: [nest-mini-drop-in-pcb](https://github.com/iMike78/nest-mini-drop-in-pcb) by [@iMike78](https://github.com/iMike78)
- **Hardware reference**: Home Assistant Voice Preview Edition
- **Community**: [Home Assistant Community Thread](https://community.home-assistant.io/t/request-alternative-to-onju-voice-drop-in-pcb-repacement/860001)
- **Teardown reference**: [iFixit Nest Audio Teardown](https://www.ifixit.com/Teardown/Google+Nest+Audio+Teardown/146986)

## Similar Projects

- [nest-mini-drop-in-pcb](https://github.com/iMike78/nest-mini-drop-in-pcb) - Google Nest Mini v2 replacement
- [Onju Voice](https://github.com/justLV/onju-voice) - Original inspiration
- [Home Assistant Voice PE](https://www.home-assistant.io/voice-pe/) - Official hardware reference

## License

This project is licensed under the **CERN Open Hardware Licence Version 2 - Strongly Reciprocal (CERN-OHL-S v2)**.

See [LICENSE](LICENSE) file for full text.

## Disclaimer

This is an independent open-source project and is not affiliated with or endorsed by Google LLC. "Google Nest Audio" is a trademark of Google LLC.

Use at your own risk. Modifying electronic devices can be dangerous. Ensure you understand the risks before proceeding.

## Support

- **Issues**: [GitHub Issues](../../issues)
- **Discussions**: [GitHub Discussions](../../discussions)
- **Community**: Home Assistant Voice Assistant thread

## Roadmap

### Phase 1: Hardware (Current)
- [x] Initial project setup
- [ ] Complete measurements from 3D scan
- [ ] Finalize component selection
- [ ] Complete PCB design
- [ ] Order prototypes

### Phase 2: Testing
- [ ] PCB bring-up and testing
- [ ] Audio quality verification
- [ ] Thermal testing
- [ ] Long-term stability testing

### Phase 3: Release
- [ ] Documentation completion
- [ ] Manufacturing files
- [ ] Assembly guide video
- [ ] First stable release

### Phase 4: Enhancements
- [ ] Alternative amplifier options
- [ ] Different enclosure compatibility
- [ ] Advanced audio features
- [ ] Community contributions

---

**Made with ❤️ by the open source community**

Want to help? Check out our [good first issues](../../issues?q=is%3Aissue+is%3Aopen+label%3A%22good+first+issue%22)!