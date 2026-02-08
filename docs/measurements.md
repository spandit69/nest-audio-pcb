# Nest Audio Measurements

This document contains all physical measurements for the Nest Audio PCB replacement project.

## Overview

**Source**: 3D scan data from Library 21c, Colorado Springs  
**Date**: [Fill in after scan]  
**Scanner**: NextEngine 3D Laser Scanner  
**Operator**: [Fill in]  
**Files**: [Link to scan files]

## Enclosure Dimensions

### External
| Dimension | Value (mm) | Notes |
|-----------|-----------|-------|
| Height | 175 | From Google specs |
| Width | 124 | From Google specs |
| Depth | 78 | From Google specs |
| Weight | 1200g | Without power adapter |

### Internal Cavity
| Dimension | Value (mm) | Notes |
|-----------|-----------|-------|
| Max PCB Length | [TBD] | From scan |
| Max PCB Width | [TBD] | From scan |
| Max PCB Thickness | [TBD] | From scan |
| Depth Available | [TBD] | From scan |

## PCB Measurements

### Main Logic Board (MLB)

#### Overall Dimensions
| Measurement | Value (mm) | Tolerance |
|-------------|-----------|-----------|
| Length | [TBD] | ±0.5mm |
| Width | [TBD] | ±0.5mm |
| Thickness | [TBD] | ±0.1mm |
| Layer Count | [TBD] | Original board |

#### Mounting Holes
Original board uses **7x T6 screws** (3.5mm across flats)

| Hole # | X Position (mm) | Y Position (mm) | Diameter (mm) |
|--------|----------------|----------------|---------------|
| 1 | [TBD] | [TBD] | [TBD] |
| 2 | [TBD] | [TBD] | [TBD] |
| 3 | [TBD] | [TBD] | [TBD] |
| 4 | [TBD] | [TBD] | [TBD] |
| 5 | [TBD] | [TBD] | [TBD] |
| 6 | [TBD] | [TBD] | [TBD] |
| 7 | [TBD] | [TBD] | [TBD] |

**Coordinate System**: Origin at top-left corner of PCB (when viewed from top)

#### Component Locations

**Power Input**
| Component | X (mm) | Y (mm) | Notes |
|-----------|--------|--------|-------|
| Barrel Jack Center | [TBD] | [TBD] | 14V input |
| Barrel Jack Diameter | [TBD] | - | Check size |

**Audio Connectors**
| Component | X (mm) | Y (mm) | Notes |
|-----------|--------|--------|-------|
| Speaker + | [TBD] | [TBD] | Spade connector |
| Speaker - | [TBD] | [TBD] | Spade connector |
| Spacing | [TBD] | - | Center-to-center |

**Data Connectors**
| Component | X (mm) | Y (mm) | Notes |
|-----------|--------|--------|-------|
| LED Flex Connector | [TBD] | [TBD] | [pin count] |
| Touch Sensor Connector | [TBD] | [TBD] | [pin count] |
| Debug Header (if any) | [TBD] | [TBD] | [pin count] |

#### Clearance Areas

**Keepout Zones**
| Area | X Position (mm) | Y Position (mm) | Size (mm) | Reason |
|------|----------------|----------------|-----------|--------|
| Speaker Magnet | [TBD] | [TBD] | [TBD] | Magnetic interference |
| Metal Frame | [TBD] | [TBD] | [TBD] | Ground plane |
| LED Window | [TBD] | [TBD] | [TBD] | Light path |

**Height Restrictions**
| Area | Max Height (mm) | Notes |
|------|----------------|-------|
| Top Side | [TBD] | Speaker clearance |
| Bottom Side | [TBD] | Enclosure clearance |
| Center Area | [TBD] | Processor heatsink |
| Edge Areas | [TBD] | Wall clearance |

### Daughterboard

#### Dimensions
| Measurement | Value (mm) |
|-------------|-----------|
| Length | [TBD] |
| Width | [TBD] |
| Thickness | [TBD] |

#### Mounting
| Feature | Value (mm) |
|---------|-----------|
| Screw Count | [TBD] |
| Screw Type | [TBD] |
| Position 1 | [TBD], [TBD] |
| Position 2 | [TBD], [TBD] |

#### Connectors
| Connector | Position (mm) | Type |
|-----------|--------------|------|
| Power Input | [TBD], [TBD] | Barrel Jack |
| Speaker 1 | [TBD], [TBD] | Spade |
| Speaker 2 | [TBD], [TBD] | Spade |

## Speaker Specifications

### Physical Dimensions
| Measurement | Value | Unit |
|-------------|-------|------|
| Driver Diameter | [TBD] | mm |
| Magnet Diameter | [TBD] | mm |
| Magnet Thickness | [TBD] | mm |
| Mounting Hole Spacing | [TBD] | mm |
| Mounting Hole Count | [TBD] | - |

### Electrical Specifications
| Parameter | Value | Notes |
|-----------|-------|-------|
| Impedance | [TBD] | Ohms |
| Power Rating | [TBD] | Watts |
| Sensitivity | [TBD] | dB/W/m |
| Frequency Range | [TBD] | Hz |

**Marking on Driver**: [Photo/scan of text on magnet]

### Mounting
| Feature | Value (mm) |
|---------|-----------|
| Mounting Tab 1 | [TBD], [TBD] |
| Mounting Tab 2 | [TBD], [TBD] |
| Mounting Tab 3 | [TBD], [TBD] |
| Screw Type | T6 |

## LED Board

### Dimensions
| Measurement | Value (mm) |
|-------------|-----------|
| Length | [TBD] |
| Width | [TBD] |
| Thickness | [TBD] |

### LED Positions
| LED # | X (mm) | Y (mm) | Notes |
|-------|--------|--------|-------|
| 1 | [TBD] | [TBD] | - |
| 2 | [TBD] | [TBD] | - |
| 3 | [TBD] | [TBD] | - |
| 4 | [TBD] | [TBD] | - |
| 5 | [TBD] | [TBD] | - |
| 6 | [TBD] | [TBD] | - |

### Connector
| Feature | Value |
|---------|-------|
| Position | [TBD], [TBD] |
| Pin Count | [TBD] |
| Pitch | [TBD] mm |

## Flex Cables

### Touch Sensor Cable
| Parameter | Value |
|-----------|-------|
| Length | [TBD] mm |
| Width | [TBD] mm |
| Connector Type | [TBD] |
| Pin Count | [TBD] |

### LED Cable
| Parameter | Value |
|-----------|-------|
| Length | [TBD] mm |
| Width | [TBD] mm |
| Connector Type | [TBD] |
| Pin Count | [TBD] |

## Power Supply

### Connector
| Parameter | Value |
|-----------|-------|
| Type | Barrel Jack |
| Outer Diameter | [TBD] mm |
| Inner Diameter | [TBD] mm |
| Length | [TBD] mm |
| Polarity | Center [TBD] |

### Specifications
| Parameter | Value |
|-----------|-------|
| Input Voltage | 100-240V AC |
| Output Voltage | 14V DC |
| Output Current | [TBD] A |
| Power Rating | [TBD] W |

## Critical Measurements for PCB Design

### Must Match Exactly
These dimensions must match the original PCB:
1. Mounting hole positions (±0.2mm)
2. Barrel jack location (±0.5mm)
3. Speaker connector spacing (±0.5mm)
4. LED connector position (±0.5mm)
5. Touch connector position (±0.5mm)

### Can Be Modified
These areas have flexibility:
1. PCB outline (within enclosure)
2. Component placement (top/bottom)
3. Trace routing
4. Test point locations
5. Programming interfaces

### Keepout Areas
No components in these zones:
1. Speaker magnet area (magnetic interference)
2. Metal mounting brackets (shorting risk)
3. LED light path
4. Touch sensor area

## Comparison with Nest Mini

| Feature | Nest Mini | Nest Audio | Difference |
|---------|-----------|-----------|------------|
| PCB Size | 80mm x 80mm | [TBD] | [TBD] |
| Speaker Size | 40mm | [TBD] | [TBD] |
| Speaker Power | 3W | [TBD] | [TBD] |
| Mounting Screws | 4x T6 | 7x T6 | [TBD] |
| Enclosure Size | Smaller | 175x124x78 | Much larger |

## 3D Scan Data

### File Locations
```
hardware/enclosure/3d-scans/
├── mlb-top.stl
├── mlb-bottom.stl
├── daughterboard.stl
├── speaker-left.stl
├── speaker-right.stl
├── led-board.stl
└── enclosure-cavity.stl
```

### Scan Resolution
- **Point Spacing**: [TBD] mm
- **Accuracy**: [TBD] mm
- **Scan Date**: [Fill in]
- **Processing Software**: [TBD]

## Measurement Verification

### Tools Used
- 3D Scanner: NextEngine Laser Scanner
- Caliper Verification: [Model]
- Software: [Measurement software]

### Accuracy Check
| Measurement | Scan Value | Caliper Value | Error |
|-------------|-----------|---------------|-------|
| PCB Length | [TBD] | [TBD] | [TBD] |
| Mounting Hole | [TBD] | [TBD] | [TBD] |
| Speaker Diameter | [TBD] | [TBD] | [TBD] |

## Updates

| Date | Change | Author |
|------|--------|--------|
|[Date] | Initial measurements from 3D scan | [Name] |
|[Date] | [Description] | [Name] |

## Notes

- All measurements in millimeters unless noted
- Coordinate system: Top-left corner = (0,0)
- Tolerance on measurements: ±0.5mm unless specified
- Please verify all measurements before ordering PCBs
- Update this document as design progresses

---

**Last Updated**: [Date]  
**Status**: Work in Progress - Pending 3D Scan
