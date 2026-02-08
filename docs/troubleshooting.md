# Troubleshooting Guide

Common issues and solutions for the Nest Audio PCB project.

## Hardware Issues

### Device Won't Power On

**Symptoms:** No LEDs, no response to buttons

**Check:**
1. **Power Input**
   - Verify 14V power supply connected
   - Check polarity (center positive)
   - Test voltage with multimeter (should be 13.5-14.5V)
   - Try different power supply

2. **Voltage Rails**
   - Check 3.3V rail (should be 3.2-3.4V)
   - Check 5V rail (should be 4.9-5.1V)
   - If no voltage, check LDO regulators

3. **Short Circuits**
   - Check resistance between power and ground
   - Look for solder bridges on ICs
   - Check for damaged components

**Solutions:**
- Replace power supply
- Reflow LDO solder joints
- Remove solder bridges with wick
- Replace damaged components

### ESP32 Not Responding

**Symptoms:** Can't flash, no serial output, not in HA

**Check:**
1. **Boot Mode**
   - Verify BOOT button held during reset
   - Check GPIO0 pulled low
   - Try different USB cable

2. **Power**
   - Ensure 3.3V present on ESP32 pins
   - Check center pad soldered (ground/thermal)
   - Verify no voltage drops under load

3. **Connections**
   - USB data lines connected properly
   - No cold solder joints
   - Crystal oscillating (32.768kHz)

**Solutions:**
- Reflow ESP32 with hot air (check all pins)
- Resolder center pad
- Replace USB cable
- Check crystal with scope

### No Audio Output

**Symptoms:** No sound from speaker, but device responds

**Check:**
1. **Amplifier Power**
   - 5V present on MAX98357
   - VDD and PVDD connected
   - Gains set correctly

2. **Speaker Connections**
   - Spade connectors tight
   - No broken wires
   - Speaker impedance correct

3. **I2S Signals**
   - BCLK present (1-3MHz)
   - LRCLK present (48kHz)
   - DIN has data

**Solutions:**
- Resolder amplifier
- Check speaker wiring
- Verify I2S config in firmware
- Test with known-good speaker

### Distorted or Quiet Audio

**Symptoms:** Sound present but quality poor

**Possible Causes:**
- Gain setting too high/low
- Power supply noise
- Ground loop
- Speaker impedance mismatch

**Solutions:**
1. Adjust gain resistors on amplifier
2. Add more decoupling capacitors
3. Improve ground plane
4. Verify speaker specs match design

### Microphones Not Working

**Symptoms:** Voice assistant doesn't respond to voice

**Check:**
1. **Physical**
   - Mics soldered correctly
   - Sound ports not blocked
   - Right orientation (sound port facing out)

2. **Electrical**
   - 3.3V present on mic pins
   - I2S connections to XMOS
   - Clock signals present

3. **Firmware**
   - Correct mic config in YAML
   - Proper I2S settings
   - Gain not too low

**Solutions:**
- Resolder microphones (heat sensitive!)
- Check XMOS firmware loaded
- Verify I2S routing in schematic
- Increase mic gain in config

### LEDs Not Working

**Symptoms:** No status indication

**Check:**
1. **Power**
   - 5V on LED power pin
   - Data line has signal
   - Ground connected

2. **Order**
   - LEDs installed in correct order
   - DI/DO chain correct
   - First LED data in connected

3. **Firmware**
   - Correct GPIO pin (GPIO5)
   - Right LED type (SK6812)
   - Proper color order (GRB)

**Solutions:**
- Check with multimeter for 5V
- Reflow LED solder joints (low heat!)
- Test LEDs one at a time
- Verify YAML configuration

### Overheating

**Symptoms:** Hot components, thermal shutdown

**Check:**
1. **Amplifier**
   - Heatsink attached
   - Thermal pad present
   - Not driving low impedance

2. **Voltage Regulators**
   - Input voltage not too high
   - Load current within spec
   - Proper heatsinking

3. **ESP32**
   - Center pad soldered
   - Not transmitting constantly
   - WiFi power appropriate

**Solutions:**
- Add heatsinks
- Improve ventilation
- Check for shorts
- Reduce transmit power
- Add thermal management to enclosure

## Firmware Issues

### Can't Connect to WiFi

**Symptoms:** Device creates AP but won't join network

**Check:**
1. **Credentials**
   - SSID correct (case-sensitive)
   - Password correct
   - No special characters causing issues

2. **Signal Strength**
   - RSSI > -70dBm
   - 2.4GHz network (not 5GHz)
   - Not too far from router

3. **Router Settings**
   - 802.11b/g/n mode enabled
   - Not using WPA3 only
   - DHCP enabled

**Solutions:**
- Re-enter WiFi credentials
- Move closer to router
- Check router settings
- Use WiFi scan to find network

### Device Offline in Home Assistant

**Symptoms:** Device not responding, entities unavailable

**Check:**
1. **Network**
   - Device has IP address
   - Pingable from HA server
   - Same subnet

2. **API**
   - Encryption key correct
   - API not disabled
   - Port not blocked

3. **Logs**
   - Check ESPHome logs
   - Look for connection errors
   - Verify HA IP address

**Solutions:**
- Re-add to HA with correct key
- Restart HA
- Check firewall rules
- Re-flash with new key

### Wake Word Not Working

**Symptoms:** Device responds to button but not voice

**Check:**
1. **Microphones**
   - Mics detected by firmware
   - Audio input visible in logs
   - Gain not too low

2. **Wake Word Setting**
   - Enabled in HA
   - Correct wake word selected
   - Voice assistant pipeline configured

3. **Pipeline**
   - STT service working
   - TTS service working
   - No errors in pipeline

**Solutions:**
- Check mic gain levels
- Re-enable wake word
- Test pipeline in HA
- Use button trigger instead

### Audio Stuttering or Dropouts

**Symptoms**: Audio cuts in and out

**Possible Causes:**
- WiFi interference
- Buffer underrun
- Network latency
- CPU overload

**Solutions:**
1. Check WiFi signal strength
2. Use wired connection if possible
3. Reduce audio quality temporarily
4. Check for interference sources
5. Add decoupling capacitors

## Assembly Issues

### Solder Bridges on ICs

**How to Fix:**
1. Apply flux to bridge area
2. Use solder wick/braid
3. Touch with clean iron tip
4. Wick will absorb excess solder
5. Check with microscope

### Cold Solder Joints

**Identification:**
- Dull, grainy appearance
- Doesn't flow smoothly
- Component moves when touched

**Fix:**
1. Add flux
2. Reheat with iron until solder flows
3. Don't move until cooled
4. Should look shiny and smooth

### Component Alignment Off

**How to Fix:**
1. Apply flux
2. Heat one corner pad
3. While molten, nudge into position
4. Hold until cooled
5. Solder remaining pins

### Damaged Component

**Prevention:**
- Use ESD protection
- Don't overheat
- Handle gently
- Check polarity before soldering

**Replacement:**
- Remove with hot air
- Clean pads
- Install new component
- Verify orientation

## Debug Procedures

### Serial Debug

**Connect:**
```bash
esphome logs nest-audio.yaml
```

**Look for:**
- Boot messages
- WiFi connection status
- Voice assistant state
- Error messages

### Voltage Testing Points

**Test Points on PCB:**
- TP1: 14V input
- TP2: 5V rail
- TP3: 3.3V rail
- TP4: GND
- TP5: I2S BCLK
- TP6: I2S LRCLK

### Signal Probing

**With Oscilloscope:**
- I2S signals (BCLK, LRCLK, DIN/DOUT)
- Power rails (noise/ripple)
- Crystal (32.768kHz)
- WiFi activity

## Getting Help

### Before Asking

1. **Check documentation**
   - This troubleshooting guide
   - Assembly guide
   - Firmware flashing guide

2. **Gather information**
   - Serial logs
   - Voltage readings
   - Photos of assembly
   - Exact error messages

3. **Try basic fixes**
   - Power cycle
   - Re-flash firmware
   - Check connections
   - Simplify config

### Where to Ask

1. **GitHub Issues**
   - For bugs and hardware issues
   - Include logs and photos
   - Be specific about problem

2. **GitHub Discussions**
   - For questions and ideas
   - General troubleshooting
   - Feature requests

3. **Home Assistant Community**
   - Voice Assistant specific
   - ESPHome questions
   - Integration help

4. **Discord/Forums**
   - Real-time help
   - Community support
   - Show-and-tell

### Good Bug Report

Include:
- [ ] Clear description of problem
- [ ] Steps to reproduce
- [ ] Expected vs actual behavior
- [ ] Serial logs (relevant parts)
- [ ] Photos of hardware
- [ ] Firmware version
- [ ] Hardware revision
- [ ] What you've already tried

## Preventing Issues

### Before Assembly
- [ ] Read all documentation
- [ ] Check BOM against received parts
- [ ] Verify PCB fabrication quality
- [ ] Prepare proper tools
- [ ] Set up ESD protection

### During Assembly
- [ ] Follow order in assembly guide
- [ ] Check polarity on every component
- [ ] Use adequate lighting
- [ ] Take breaks to avoid fatigue
- [ ] Test at each stage if possible

### Before First Power-On
- [ ] Visual inspection with microscope
- [ ] Check for solder bridges
- [ ] Verify no shorts with multimeter
- [ ] Double-check power connections
- [ ] Have fire extinguisher nearby

## Safety First

⚠️ **Remember:**
- Always unplug before modifying
- Use ESD protection
- Work in ventilated area
- Wear safety glasses
- Keep workspace organized
- Don't work when tired

## Common Error Messages

### "Failed to initialize I2S"
**Cause:** I2S pins not connected or wrong configuration
**Fix:** Check schematic and YAML for pin assignments

### "Microphone not found"
**Cause:** Mics not detected on I2S bus
**Fix:** Check mic soldering and I2S connections

### "Voice assistant failed to start"
**Cause:** Pipeline error or mic issue
**Fix:** Check HA pipeline, verify mic working

### "Connection refused"
**Cause:** Wrong API key or HA can't reach device
**Fix:** Verify encryption key, check network

---

**Still stuck?** Open an issue on GitHub with your logs and photos!
