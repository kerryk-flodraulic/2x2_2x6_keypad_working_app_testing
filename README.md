
---
# AARCOMM Virtualized RCPU – Flutter CAN Keypad Interface

This Flutter application simulates a virtual handheld controller for CAN-based diagnostic and control systems. It emulates two Blink Marine keypads (2x2 and 2x6) and transmits structured CAN messages via Bluetooth to devices such as the Axiomatic CAN-to-Bluetooth converter or Puisi MCBox. The app is ideal for testing, QA automation, and diagnostics in J1939 environments.

---

## Features

- Virtual keypad interface for PKP2200 (2x2) and PKP2600 (2x6)
- Real-time CAN frame generation with 8-byte payloads
- Bluetooth Low Energy (BLE) scanning, filtering, and connection
- Press and release simulation of button states mapped to CAN frame bits
- Live CAN frame log with timestamp, direction, CAN ID, data, and button info
- Multi-mode Auto Test feature with:
  - Press & release simulation of all keypad buttons
  - Configurable test speed (Slow / Normal / Fast)
  - Visual key highlighting during test
  - Test summary output
- Reset, pause, clear, and export log options
- Support for CAN monitoring tools (e.g., Kvaser CANking, PCAN-View)

---

## Setup Instructions

1. **Clone the repository**

```bash
git clone https://github.com/your-username/aarcomm-virtual-rcpu.git
cd aarcomm-virtual-rcpu
````

2. **Install dependencies**

```bash
flutter pub get
```

3. **Connect hardware**

* Connect to a CAN device such as:

  * Axiomatic CAN-to-Bluetooth Converter
  * Puisi MCBox CAN gateway
* Ensure your hardware is powered and advertising over BLE

4. **Run the app**

```bash
flutter run
```

---

## Hardware Requirements

* CAN interface hardware (e.g., MCBox, Axiomatic BLE-CAN gateway)
* External power supply if required by device
* Mobile or desktop system with BLE support

---

## Key Mappings

### PKP2200 (2x2 Keypad)

| Button | Action         | CAN Byte | Bit Position |
| ------ | -------------- | -------- | ------------ |
| K1     | Power On       | 0        | 0            |
| K2     | Power Off      | 0        | 1            |
| K3     | Emergency Stop | 0        | 2            |
| K4     | Reset          | 0        | 3            |

### PKP2600 (2x6 Keypad)

| Button | Action             | CAN Byte | Bit Position |
| ------ | ------------------ | -------- | ------------ |
| F1     | Water Pump On      | 0        | 0            |
| F2     | Water Pump Off     | 0        | 1            |
| F3     | Engine On          | 0        | 2            |
| F4     | Engine Off         | 0        | 3            |
| F5     | Boom Up            | 0        | 4            |
| F6     | Boom Down          | 0        | 5            |
| F7     | Door Unlock        | 1        | 0            |
| F8     | Door Lock          | 1        | 1            |
| F9     | Vacuum On          | 1        | 2            |
| F10    | Vacuum Off         | 1        | 3            |
| F11    | Tank Raise / Dozer | 1        | 4            |
| F12    | Tank Lower / Dozer | 1        | 5            |

---

## Project Structure

* `main.dart` – UI layout, state management, keypad rendering, and log display
* `bluetooth.dart` – Bluetooth scanning, connecting, message sending
* `crc32.dart` – Utility for CRC32 framing (if applicable)
* `assets/` – Optional: image or configuration assets

---

## Future Improvements

* CSV export of CAN log
* Integration with external test suites
* Cloud sync of test logs
* Customizable control labels per device

---

