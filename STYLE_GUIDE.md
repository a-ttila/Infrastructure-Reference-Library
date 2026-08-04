NetBox Device Library Style Guide
Version: 1.0
Author: Attila Bolemányi
Purpose:
This document defines the engineering principles used when creating NetBox Device Type definitions. The goal is to build a consistent, vendor-independent device library that accurately represents physical hardware while remaining intuitive to maintain over many years.

1. General Philosophy
The Device Type is a description of physical hardware.
It must never contain information that belongs to an individual device instance.
A Device Type shall describe:
•	Physical interfaces
•	Console ports
•	Management ports
•	Power supplies
•	Fan modules
•	Module bays
•	Inventory items (when appropriate)
•	Physical dimensions
A Device Type shall never describe:
•	Hostname
•	Serial number
•	Asset tag
•	Rack position
•	Site
•	IP addresses
•	VLAN configuration
•	Stacking membership
•	Software version
Those belong to Device objects.

2. Golden Rule
Model reality.
The physical hardware always has priority over software limitations.
If a connector exists on the chassis, it should normally exist in the Device Type.

3. Naming Convention
Whenever possible, use the vendor’s native CLI naming.
Examples:
Cisco
GigabitEthernet1/0/1
TenGigabitEthernet1/0/1
FortyGigabitEthernet1/0/1
HundredGigE1/0/1
Aruba CX
1/1/1
1/1/2
FortiGate
port1
port2
Linux
eth0
ens192
Never invent simplified names simply because they look shorter.

4. Management Interfaces
Use the hardware name whenever it is well defined.
Examples:
mgmt0
Management1
OOB
MGMT
Do not rename interfaces to achieve artificial consistency.
Consistency comes from preserving the hardware, not hiding it.

5. Console Ports
Always model every console connector.
Examples:
Console RJ45
Console USB
Console MiniUSB

6. USB Ports
USB ports should be modelled whenever they are externally accessible.
Recommended naming:
USB
USB-A
USB-C

7. Alarm Ports
External alarm connectors shall be modelled.
Recommended naming:
Alarm

8. Combo Interfaces
Combo ports are represented by their physical connectors.
Example:
GigabitEthernet1/0/21C
GigabitEthernet1/0/21F
Where
•	C = Copper
•	F = Fiber
Documentation should state that only one connector may be active simultaneously.

9. Power Supplies
Power supplies shall always be represented individually.
Examples
PSU1
PSU2
Never use
Power Supply 1
unless this is the vendor’s official naming.

10. Fan Modules
Represent every field-replaceable fan separately.
Examples
Fan1
Fan2
Fan3

11. Module Bays
Whenever a device supports removable modules, they should be represented as module bays rather than ordinary interfaces.

12. Inventory Items
Accessories that are replaceable but not independently connected should normally become Inventory Items.
Examples
•	SSD
•	CompactFlash
•	TPM
•	Internal battery

13. Stacking
Stack capability belongs to the hardware documentation.
Stack membership belongs to Device objects.
Never create separate Device Types for stack members.

14. Comments
Every YAML file should begin with a descriptive comment block.
Example:
###########################################################################
# Device Type : D-Link DXS-3400-24SC
# Vendor      : D-Link
# Version     : 1.0
# Created     : 2026-08-04
#
# Notes
#   Combo interfaces are modelled as separate Copper/Fiber connectors.
###########################################################################
Comments are intended for engineers and future maintainers.

15. YAML Formatting
•	Use two-space indentation.
•	Group similar objects together.
•	Keep interface numbering in physical order.
•	Keep management and console ports after data interfaces.
•	Keep power supplies and fans at the end.
•	Keep the file readable before making it compact.

16. Engineering Principle
A Device Type is infrastructure documentation.
It should allow an engineer who has never seen the hardware to understand the physical device without opening the vendor’s manual.
Accuracy is more important than speed.
Consistency is more important than convenience.
The library is intended to remain maintainable for decades.
