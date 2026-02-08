# Flashing Guide

This guide covers flashing the ESPHome firmware onto your Nest Audio PCB.

## Prerequisites

### Hardware
- [ ] Assembled Nest Audio PCB
- [ ] USB-C cable (data capable, not charge-only)
- [ ] 14V power supply (optional for initial flash)

### Software
- [ ] ESPHome installed (`pip install esphome`)
- [ ] Or ESPHome Dashboard/Add-on if using Home Assistant
- [ ] USB-to-UART drivers (if needed)
- [ ] Web browser (for WiFi provisioning)

## Methods

### Method 1: USB-C Direct Programming (Recommended)

The ESP32-S3 supports USB-OTG and can be programmed directly via USB-C.

#### Steps:

1. **Prepare the Board**
   - Connect USB-C cable to board
   - Do NOT connect 14V power yet (unless testing)

2. **Enter Boot Mode**
   - Hold BOOT button (GPIO0)
   - Press and release RESET button
   - Release BOOT button
   - Board is now in download mode

3. **Flash ESPHome**
   ```bash
   # Navigate to firmware directory
   cd nest-audio-pcb/firmware/esphome
   
   # Flash the configuration
   esphome run nest-audio.yaml
   ```

4. **Or use ESPHome Dashboard**
   - Open ESPHome Dashboard
   - Click "Install" on nest-audio device
   - Select "Plug into this computer"
   - Wait for upload to complete

5. **First Boot**
   - After flashing, press RESET button
   - Board will boot into normal mode
   - LED should light up indicating status

### Method 2: Serial Programming (Backup Method)

If USB-C doesn't work, use the programming header.

#### Wiring:
```
PC USB-UART → PCB Header
---------------------------
GND         → GND
TX          → RX (GPIO20)
RX          → TX (GPIO21)
3.3V        → 3.3V (DO NOT USE 5V!)
```

#### Steps:

1. **Connect Programmer**
   - Wire according to diagram above
   - Double-check connections
   - Connect GND first

2. **Enter Boot Mode**
   - Hold BOOT button
   - Briefly press RESET
   - Release BOOT

3. **Flash Firmware**
   ```bash
   esphome run nest-audio.yaml --device /dev/ttyUSB0
   # On Windows: --device COM3 (check Device Manager)
   ```

4. **Disconnect and Reboot**
   - Remove programmer
   - Press RESET button
   - Device should boot normally

## First-Time Setup

### WiFi Provisioning

After first flash, the device will create an access point:

1. **Connect to AP**
   - SSID: `NestAudio Voice`
   - Password: `nestaudio123` (change in YAML)

2. **Configure WiFi**
   - Open browser, go to `192.168.4.1`
   - Select your WiFi network
   - Enter password
   - Click "Save"

3. **Connect to Home Assistant**
   - Device will appear in Home Assistant automatically
   - Look for "ESPHome" integration
   - Click "Configure" and follow prompts

### API Encryption Setup

Before first flash, create secrets file:

```yaml
# secrets.yaml
api_encryption_key: "YOUR_GENERATED_KEY_HERE"
ota_password: "YOUR_OTA_PASSWORD_HERE"
wifi_ssid: "YourWiFiSSID"
wifi_password: "YourWiFiPassword"
wifi_ap_password: "APModePassword123"
```

Generate encryption key:
```bash
openssl rand -base64 32
```

## Troubleshooting

### "Failed to connect to ESP" Error

**Solutions:**
1. Check USB cable (must be data cable)
2. Verify drivers installed
3. Ensure board is in boot mode
4. Try different USB port
5. Check Device Manager (Windows) for correct COM port

### Device Not Appearing in Home Assistant

**Check:**
1. Device connected to same network as HA
2. API encryption key matches
3. Check ESPHome logs for connection errors
4. Restart Home Assistant

### LED Not Lighting Up

**Verify:**
1. Correct GPIO pin in YAML (GPIO5)
2. 5V present on LED power rail
3. Data line connected properly
4. Try `esphome logs` to see device output

### Can't Enter Boot Mode

**Try:**
1. Hold BOOT while plugging in USB
2. Use serial method instead
3. Check BOOT button connection
4. Verify GPIO0 is pulled low

## Updating Firmware

### OTA Updates (After First Flash)

```bash
# From project directory
esphome run nest-audio.yaml

# Or in ESPHome Dashboard
# Click "Install" → "Wirelessly"
```

### Factory Reset

If device becomes unresponsive:

1. **Via Button**
   - Hold BOOT button for 10 seconds
   - Device will reset to factory defaults

2. **Via Home Assistant**
   - Go to device page
   - Press "Factory Reset" button

3. **Re-flash**
   - Use USB-C method above
   - Will erase all settings

## Serial Monitoring

View device logs:

```bash
# Via USB
esphome logs nest-audio.yaml

# Or use ESPHome Dashboard
# Click "Logs" button
```

## Advanced Options

### Safe Mode

If firmware is crashing:

1. Press RESET 10 times rapidly
2. Device enters safe mode
3. Connect to "NestAudio Voice Fallback" AP
4. Re-flash working firmware

### Enable Debug Logging

Add to YAML for verbose output:
```yaml
logger:
  level: VERY_VERBOSE
  logs:
    voice_assistant: DEBUG
    i2s_audio: DEBUG
```

### Backup Configuration

Always keep backup:
```bash
# Export current config
esphome config nest-audio.yaml > backup.yaml

# Save secrets separately
```

## Post-Flash Verification

### Basic Functionality Test

1. **WiFi Connection**
   - Check router for connected device
   - Verify IP address assigned

2. **Home Assistant Integration**
   - Device appears in ESPHome integration
   - All entities visible
   - No errors in logs

3. **Audio Test**
   - Use "Play Media" service
   - Test speaker output
   - Verify volume control works

4. **Voice Assistant**
   - Enable wake word
   - Test "Hey Jarvis" or custom wake word
   - Verify response playback

## Next Steps

After successful flash:
1. Install in Nest Audio enclosure
2. Connect speakers and power
3. Fine-tune audio settings
4. Enjoy your open-source voice assistant!

## Support

- **ESPHome Docs**: https://esphome.io/
- **Voice Assistant Docs**: https://esphome.io/components/voice_assistant.html
- **GitHub Issues**: Report bugs here
- **Community**: Home Assistant Discord/forums
