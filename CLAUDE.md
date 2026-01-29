# KiCAD Projects

Repository for KiCad electronic design projects.

**KiCad Version:** 9.0
**Libraries Location:** `C:\Users\ADMIN\Documents\KiCad\libraries\`

## External Libraries Installed

### Seeed Studio OPL KiCad Library
- **Location:** `C:\Users\ADMIN\Documents\KiCad\libraries\OPL_Kicad_Library\`
- **Source:** https://github.com/Seeed-Studio/OPL_Kicad_Library
- **Key Components:**
  - XIAO ESP32-C6 (DIP and SMD footprints)
  - XIAO ESP32-S3, ESP32-C3, RP2040, nRF52840, SAMD21, RA4M1, RP2350, MG24
  - Grove Vision AI V2
  - Wio Series modules

**To add to KiCad:**
1. Open Schematic Editor → Preferences → Manage Symbol Libraries
2. Add: `OPL_Kicad_Library\Seeed Studio XIAO Series Library\Seeed_Studio_XIAO_Series.kicad_sym`
3. Open PCB Editor → Preferences → Manage Footprint Libraries
4. Add folder: `OPL_Kicad_Library\Seeed Studio XIAO Series Library\`

## Projects

### IR_Obstacle_Sensor

Infrared obstacle detection sensor module based on LM393 comparator.

**Files:**
- `IR_Obstacle_Sensor.kicad_sch` - Full schematic with all components
- `IR_Obstacle_Sensor.kicad_sym` - Reusable block symbol (3-pin: VCC, GND, DO)

**Circuit Description:**
- IR LED emits infrared light
- Phototransistor receives reflected IR
- LM393 comparator compares signal against adjustable threshold (VR1)
- Digital output (DO) indicates obstacle presence
- Power LED indicates VCC present
- Switch LED indicates detection state

**Components:**

| Reference | Value | Description |
|-----------|-------|-------------|
| D1 | Power_LED | Power indicator LED |
| R1 | 1K | Current limiter for power LED |
| C1 | 100nF | Decoupling capacitor |
| R2 | 100 | IR LED current limiter |
| R3 | 10K | Phototransistor pull-up |
| VR1 | 10K | Threshold adjustment potentiometer |
| D2 | IR_LED | Infrared emitter |
| Q1 | Phototransistor | IR receiver |
| C2 | 100nF | Filter capacitor |
| U1 | LM393 | Comparator IC |
| R4 | 10K | Output pull-up resistor |
| D3 | Switch_LED | Detection indicator LED |
| R5 | 1K | Current limiter for switch LED |
| J1 | CON3 | 3-pin connector (VCC, GND, DO) |

**Connector Pinout (J1):**
1. VCC - Power supply (3.3V-5V)
2. GND - Ground
3. DO - Digital output (active low when obstacle detected)

**To use the reusable symbol:**
1. Add `IR_Obstacle_Sensor.kicad_sym` to your symbol libraries
2. Search for "IR_Obstacle_Sensor" when adding components
3. Connect VCC, GND, and DO pins to your circuit

## KiCad 9.0 Notes

- **Symbol Libraries:** Schematic Editor → Preferences → Manage Symbol Libraries
- **Footprint Libraries:** PCB Editor → Preferences → Manage Footprint Libraries
- **Plugin Manager:** Main window → Plugin and Content Manager

## Related Infrastructure

This workstation connects to the home infrastructure documented in:
- **Repository:** https://github.com/coachsmith50/infrastructure-docs
- **Secrets:** Stored in `CLAUDE.local.md` on NAS

### Network Context

| Device | IP | Purpose |
|--------|-----|---------|
| Windows Workstation | Local | KiCad development, Claude Code |
| Proxmox Host | 192.168.18.117 | Hypervisor, NAS storage |
| Home Assistant | 192.168.18.119 | Automation (potential ESP32-C6 integration) |

## Future Projects

Potential projects using Seeed Studio XIAO ESP32-C6:
- Home automation sensors (connected to Home Assistant)
- Custom Zigbee/Thread devices
- Low-power battery-operated sensors
