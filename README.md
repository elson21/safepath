# Stalker Tracker - WiFi Stalking Detection Device

A wearable device that detects potential stalking by monitoring persistent Wi-Fi MAC addresses in your vicinity.

## 🎯 Concept

Instead of tracking a victim after an incident, this device **prevents incidents** by warning the wearer when someone is persistently following them based on WiFi signature patterns.

## 🎯 End Goal: Hybrid System

**Device (Wearable):**
- Does the grunt work: WiFi scanning, MAC tracking, local alerts
- Always-on, low power, discreet
- Works standalone OR paired with phone

**Mobile App (Companion):**
- Configuration: sensitivity, ignore lists, alert preferences
- Alert history and pattern logging
- **Parental controls**: Monitor child's alerts remotely
- GPS tracking when alert triggered
- Export data for analysis
- Cloud sync for multiple devices

**Use Cases:**
- Kids wear device, parents monitor via app
- Adults use device standalone with optional app features
- Family members can share ignore lists across devices

## 🚀 Development Roadmap

This is an **ongoing project** being built iteratively from prototype to production.

### Phase 1: 🧪 Proof of Concept (MVP)
**Status:** ⏳ In Progress  
**Goal:** Prove the detection algorithm works on standard ESP32 dev board

- [ ] Basic WiFi scanning in promiscuous mode
- [ ] MAC address extraction from probe requests
- [ ] Tracking algorithm with 15-minute sliding window
- [ ] Threshold detection (5+ occurrences)
- [ ] LED alert implementation
- [ ] Serial debug output for testing
- [ ] Field testing for false positive rates

**Current Hardware:** ESP32-C3 DevKit on breadboard with built-in LED

### Phase 2: 📦 Prototype Device
**Status:** ⬜ Not Started  
**Goal:** Build first portable version in small enclosure

- [ ] Add vibration motor for discreet alerts
- [ ] Integrate LiPo battery (450mAh)
- [ ] Power optimization (deep sleep, duty cycling)
- [ ] 3D printed enclosure design (small box form factor)
- [ ] USB-C charging circuit
- [ ] Real-world battery life testing (target: 4-6 hours)

**Target Hardware:** ESP32-C3 module + components in 3D printed case

### Phase 3: ⚡ Feature Enhancement
**Status:** ⬜ Not Started  
**Goal:** Add advanced features for better usability

- [ ] Ignore list for known devices (home WiFi, family phones)
- [ ] Adjustable sensitivity settings
- [ ] Bluetooth connection to phone app (configuration)
- [ ] Alert patterns (different vibrations for threat levels)
- [ ] SPIFFS/LittleFS for persistent storage

### Phase 4: 🎨 Custom PCB Design
**Status:** ⬜ Not Started  
**Goal:** Design production-ready circuit board

- [ ] Schematic design in KiCAD
- [ ] Component selection (ESP32-C3-MINI-1, battery protection, LDO)
- [ ] PCB layout optimization for size
- [ ] PCB antenna design (or external antenna decision)
- [ ] Order prototype PCBs (JLCPCB)
- [ ] SMD assembly and testing

### Phase 5: 👗 Wearable Form Factor
**Status:** ⬜ Not Started  
**Goal:** Transform into wearable pendant

- [ ] Miniaturized enclosure design (30×40×8mm target)
- [ ] Wearable attachment mechanism (clip, chain, etc.)
- [ ] Drop test and durability testing
- [ ] Water resistance considerations
- [ ] Multiple design iterations

### Phase 6: 🧠 Algorithm Refinement
**Status:** ⬜ Not Started  
**Goal:** Improve detection accuracy

- [ ] Signal strength (RSSI) analysis
- [ ] Vendor OUI filtering (ignore randomized MACs)
- [ ] Multi-device pattern recognition
- [ ] Adaptive thresholds based on environment
- [ ] Machine learning exploration (optional)

### Phase 7: 📱 Companion App & Parental Controls
**Status:** ⬜ Not Started  
**Goal:** Mobile app for configuration, monitoring, and parental features

- [ ] Bluetooth communication protocol (device ↔ app)
- [ ] User authentication system
- [ ] Settings interface (thresholds, ignore list, alert modes)
- [ ] Real-time alert notifications to parent's phone
- [ ] Alert history logging with timestamps
- [ ] GPS location capture when alert triggered
- [ ] **Parental dashboard**: Monitor child's device remotely
- [ ] **Multi-device support**: Parents track multiple children
- [ ] Shared ignore lists across family devices
- [ ] Export data for analysis (CSV/JSON)
- [ ] Cloud backend for sync (Firebase/AWS?)
- [ ] Cross-platform app (Flutter/React Native)

### Phase 8: 🔐 Security & Privacy
**Status:** ⬜ Not Started  
**Goal:** Ensure data privacy and secure communication

- [ ] End-to-end encryption for device ↔ app communication
- [ ] Secure cloud storage (encrypted at rest)
- [ ] User data privacy compliance (GDPR, COPPA for children)
- [ ] Parental consent mechanisms
- [ ] Local-only mode (no cloud sync option)
- [ ] Penetration testing
- [ ] Security audit and documentation

## 🔧 Current Hardware Setup

**Prototype Phase 1:**
- ESP32-C3 DevKit board
- Built-in LED for alerts
- USB cable for power and programming
- Breadboard development environment

**Future Hardware (Phase 2+):**
- Small 3D printed enclosure
- LiPo battery for portability
- Vibration motor
- Eventually: Custom PCB in pendant form factor

## 🧮 Detection Logic

1. Scan WiFi probe requests every few seconds
2. Store MAC addresses with timestamps
3. Count occurrences within 15-minute sliding window
4. Alert if same MAC appears 5+ times (threshold)
5. Clean up old entries to manage memory

## 🎁 Planned Features (Post-MVP)

**Device Features:**
- Vibration motor for discreet alerts
- Multiple alert patterns (different threat levels)
- Standalone operation without phone
- Water resistance for daily wear

**App Features:**
- Parental monitoring dashboard
- Real-time alert push notifications
- GPS location when alert triggered
- Alert history with map visualization
- Custom threshold configurations per environment
- Shared family ignore lists
- Multi-device management (track multiple kids)
- Emergency contact integration
- Cloud sync and backup

## 📐 Target Final Form Factor

- Wearable pendant (30mm × 40mm × 8mm)
- 450mAh LiPo battery
- USB-C charging
- 4-6 hours continuous operation

## 🔍 Background

Inspired by the [Chasing Your Tail](https://github.com/ArgeliusLabs/Chasing-Your-Tail-NG) project but miniaturized for personal wearable use, particularly for vulnerable individuals like children.

**Key Differences from Chasing Your Tail:**
- Ultra-portable vs. Raspberry Pi setup
- Real-time alerts vs. post-analysis reports
- Simple threshold detection vs. complex GPS/WiGLE integration
- Prevention focus vs. evidence gathering

## 📝 License

MIT

## 👤 Author

Created as a personal safety project and YouTube channel content.

---

**[Current Phase: 1 - Proof of Concept]**  
**Last Updated:** October 25, 2025