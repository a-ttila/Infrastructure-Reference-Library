# Infrastructure Reference Library

*A vendor-independent, engineering-focused NetBox Device Type library.*

---

## Philosophy

Infrastructure documentation should describe the real hardware, not merely satisfy the limitations of management software.

This repository contains carefully engineered NetBox Device Type definitions that prioritize physical accuracy, long-term maintainability and consistent modelling across multiple hardware vendors.

The objective is not to reproduce manufacturer inconsistencies but to provide a coherent reference model suitable for enterprise infrastructure documentation.

---

## Design Goals

- Hardware-first modelling
- Vendor-independent engineering principles
- Native CLI interface naming whenever practical
- Long-term maintainability
- Consistent modelling across all vendors
- Human-readable YAML
- Version controlled
- Community friendly

---

## Design Principles

Every Device Type in this repository follows the accompanying `STYLE_GUIDE.md`.

The most important principles are:

- Model physical reality.
- Preserve native interface names.
- Document every externally accessible connector.
- Separate hardware definition from device configuration.
- Prefer engineering consistency over convenience.

---

## Repository Structure

```
Infrastructure-Reference-Library/

├── README.md
├── STYLE_GUIDE.md
├── CHANGELOG.md
├── LICENSE
│
├── D-Link/
├── Cisco/
├── Aruba/
├── HPE/
├── Fortinet/
├── Dell/
├── APC/
├── Eaton/
└── docs/
```

---

## Supported Vendors

- APC
- Aruba
- Cisco
- Dell
- D-Link
- Eaton
- Fortinet
- Hewlett Packard Enterprise (HPE)

Additional vendors will be added over time.

---

## Modelling Philosophy

This library intentionally models physical hardware rather than software abstractions.

Examples include:

- Separate modelling of combo copper/fiber connectors.
- Individually represented hot-swappable power supplies.
- Individually represented fan modules.
- Dedicated management interfaces.
- All console connectors.
- External USB connectors where appropriate.

The goal is to produce documentation that accurately represents the device as seen by an engineer standing in front of the rack.

---

## Quality Objectives

Every Device Type should:

- follow the STYLE_GUIDE
- use consistent naming
- be easy to read
- be internally documented
- accurately represent the physical hardware
- be suitable for production environments

Quality is always preferred over quantity.

---

## Contributing

Contributions are welcome.

Before submitting a Device Type, please ensure that it:

- follows the STYLE_GUIDE
- has been verified against official vendor documentation
- has been tested in NetBox
- follows the repository naming conventions

---

## Roadmap

Initial milestones:

- [x] Repository structure
- [x] STYLE_GUIDE
- [ ] D-Link DXS-3400-24SC
- [ ] FortiGate 600E
- [ ] HPE 5940
- [ ] Aruba 8360
- [ ] Cisco Catalyst 9500

---

## License

This repository is distributed under the MIT License.

---

## Motto

> *Model hardware as it exists, not as software wishes it existed.*

---

## Author

Attila Bolemányi

Hungary

2026
