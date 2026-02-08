# Assembly Guide

## Overview

This guide will walk you through assembling the Nest Audio drop-in PCB.

**Skill Level**: Intermediate  
**Time Required**: 2-3 hours  
**Tools Required**: See Tools section below

## Prerequisites

Before you begin:
1. PCB is fabricated and tested
2. All components from BOM are received
3. Disassembled Nest Audio enclosure ready
4. Workspace with good lighting and ESD protection

## Tools Required

### Essential
- [ ] Temperature-controlled soldering station (350°C max)
- [ ] Hot air rework station
- [ ] Fine tip tweezers (ESD-safe)
- [ ] Magnifying lamp or microscope
- [ ] Flux (no-clean type)
- [ ] Solder wire (63/37 or lead-free, 0.5mm)
- [ ] Solder wick/braid
- [ ] Isopropyl alcohol (99%)
- [ ] Anti-static mat and wrist strap

### Optional but Helpful
- [ ] PCB holder/vice
- [ ] Fine tip solder sucker
- [ ] Thermal camera (for hot spots)
- [ ] Multimeter with continuity test
- [ ] Oscilloscope (for debugging)

## Component Installation Order

Install components in this order (lowest profile to highest):

### Step 1: Passive Components (SMD)
**Priority**: High  
**Difficulty**: Easy

1. **Resistors and Capacitors (0603/0805)**
   - Apply flux to pads
   - Place component with tweezers
   - Tack one side with soldering iron
   - Solder other side
   - Remove excess solder with wick if needed

2. **Ferrite Beads**
   - Same procedure as resistors
   - Note polarity marking (if applicable)

3. **Crystals**
   - Handle carefully (fragile)
   - Ensure proper orientation
   - Check ground connections

### Step 2: Small ICs and Regulators
**Priority**: High  
**Difficulty**: Medium

1. **LDO Regulators (SOT-23)**
   - Apply flux to pads
   - Align component (check pin 1 marking)
   - Tack one corner pin
   - Adjust alignment if needed
   - Solder remaining pins

2. **MOSFETs (SOT-23)**
   - Same as LDOs
   - Verify orientation with datasheet

### Step 3: Power Components
**Priority**: High  
**Difficulty**: Medium

1. **Buck Converter (TPS54202)**
   - Apply paste flux to all pads
   - Position IC with tweezers
   - Use hot air at 300°C
   - Heat until solder flows (30-60 seconds)
   - Check alignment and solder joints

2. **Inductor (4.7uH)**
   - Hand solder with iron
   - Ensure good thermal connection

### Step 4: Microcontrollers (QFN Packages)
**Priority**: Critical  
**Difficulty**: Hard

⚠️ **WARNING**: These are the most difficult components. Take your time.

1. **ESP32-S3R8 (QFN-56)**
   - Apply solder paste to center pad and perimeter
   - Position IC carefully (check pin 1 marking)
   - Use hot air at 280-300°C
   - Heat evenly around all sides
   - Verify no bridged pins with microscope
   - Check center pad connection (critical for heat dissipation)

2. **XMOS XU316 (QFN-60)**
   - Same procedure as ESP32
   - Extra care with 60 pins
   - Check all corners for proper seating

### Step 5: Audio Amplifier
**Priority**: High  
**Difficulty**: Medium

1. **MAX98357 (TQFN-16)**
   - Hot air soldering recommended
   - Check exposed pad connection (thermal and electrical)
   - Verify no solder bridges on fine pitch pins

### Step 6: Connectors
**Priority**: Medium  
**Difficulty**: Easy

1. **USB-C Connector**
   - Apply flux
   - Position and tack one ground pin
   - Check alignment
   - Solder all pins
   - Reinforce mechanical mounting tabs

2. **Barrel Jack**
   - Through-hole mounting
   - Solder from top and bottom for strength

3. **Pin Headers**
   - Insert from top
   - Solder from bottom
   - Check for straightness

### Step 7: LEDs and Microphones
**Priority**: Medium  
**Difficulty**: Medium

1. **SK6812 RGB LEDs (6x)**
   - ⚠️ **HEAT SENSITIVE** - Use low temperature (280°C max)
   - Check polarity (DI/DO pins)
   - Install in correct order for data chain
   - Test after each LED if possible

2. **MEMS Microphones (2x)**
   - Use minimal heat
   - Check orientation (sound port direction)
   - Ensure clean solder joints (affects audio quality)

### Step 8: Final Components
**Priority**: Low  
**Difficulty**: Easy

1. **Push Buttons (2x)**
   - Through-hole
   - Check alignment with enclosure

2. **Programming Header (Optional)**
   - Can be omitted if using USB-C for programming

## Post-Assembly Checks

### Visual Inspection
- [ ] No solder bridges on IC pins
- [ ] All components properly oriented
- [ ] No cold solder joints
- [ ] No damaged components
- [ ] Clean flux residue with isopropyl alcohol

### Electrical Testing
Use multimeter to check:
- [ ] No shorts between power rails
- [ ] Correct voltage on 3.3V rail
- [ ] Correct voltage on 5V rail
- [ ] Continuity on critical traces
- [ ] Ground connections

### Power-On Test
Before installing in enclosure:
1. Connect 14V power supply
2. Check current draw (< 100mA idle)
3. Check 3.3V and 5V rail voltages
4. Look for hot components
5. No magic smoke = good!

## Common Issues

### ESP32 Not Responding
- Check center pad soldering (ground/heat sink)
- Verify 3.3V regulator output
- Check USB-C data lines

### No Audio Output
- Verify amplifier power (5V)
- Check speaker connections
- Verify I2S signals with scope

### LEDs Not Working
- Check 5V supply to LED chain
- Verify data line continuity
- Check LED polarity

### Microphone Not Working
- Verify 3.3V supply
- Check I2S connections to XMOS
- Verify microphone orientation

## Cleaning

After assembly and testing:
1. Clean all flux residue with 99% isopropyl alcohol
2. Use soft brush for stubborn areas
3. Let dry completely before powering
4. Optional: Apply conformal coating for protection

## Next Steps

After successful assembly:
1. Proceed to [Flashing Guide](flashing-guide.md)
2. Test basic functionality
3. Install in Nest Audio enclosure
4. Configure with Home Assistant

## Troubleshooting Resources

- [ESPHome Voice Assistant Documentation](https://esphome.io/components/voice_assistant.html)
- [Home Assistant Voice Setup](https://www.home-assistant.io/voice/)
- GitHub Issues: Report problems here
- Community: Home Assistant forums

## Safety Notes

⚠️ **Important Safety Information:**
- Always wear safety glasses when soldering
- Work in well-ventilated area
- Use ESD protection
- Hot components can cause burns
- Unplug power before making modifications
- Double-check polarity before applying power

## Support

Having trouble?
- Check [Troubleshooting Guide](troubleshooting.md)
- Open an issue on GitHub
- Ask in the Home Assistant community

**Good luck with your build!**
