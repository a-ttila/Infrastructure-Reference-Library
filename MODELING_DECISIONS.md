# Modeling Decisions

This document records the reasoning behind modelling decisions used throughout the Infrastructure Reference Library.

The purpose is to preserve engineering intent.

Rules are defined in `STYLE_GUIDE.md`.

This document explains **why** those rules exist.

---

# MDR-001

## Use native CLI interface names

### Decision

Interfaces should use the vendor's native CLI names whenever practical.

### Rationale

Engineers troubleshoot devices through the CLI.

Matching NetBox to the CLI eliminates unnecessary mental translation.

Example

Cisco

```
GigabitEthernet1/0/24
```

instead of

```
Port24
```

---

# MDR-002

## Model physical reality

### Decision

If a connector exists on the chassis, it should normally exist in NetBox.

### Rationale

The objective is to document hardware rather than software.

A technician standing in front of the rack should recognize the equipment immediately.

---

# MDR-003

## Combo ports are separate connectors

### Decision

Copper and Fiber sides of Combo interfaces are represented separately.

Example

```
GigabitEthernet1/0/21C
GigabitEthernet1/0/21F
```

### Rationale

Although only one side can be active, both physical connectors exist.

Infrastructure documentation should describe the chassis, not only the forwarding plane.

---

# MDR-004

## Device Types contain only hardware

### Decision

Device Types never contain deployment-specific information.

### Excluded

- hostname
- rack
- serial number
- stack member
- IP address
- asset tag

### Rationale

These belong to Device objects.

---

# MDR-005

## Stacking is configuration, not hardware

### Decision

Stack capability belongs to the Device Type.

Stack membership belongs to Device objects.

### Rationale

One Device Type should support standalone and stacked deployments.

---

# MDR-006

## Every replaceable component is represented

### Decision

Hot-swappable components should be modelled individually.

Examples

- PSU1
- PSU2
- Fan1
- Fan2
- Fan3

### Rationale

Maintenance documentation should reflect serviceable hardware.

---

# MDR-007

## Human readability has priority

### Decision

YAML files should be written for engineers.

### Rationale

Storage is inexpensive.

Engineering time is not.

Readable YAML is easier to review, maintain and troubleshoot.

---

# Future Decisions

This document is intentionally incomplete.

Every significant modelling discussion should result in a new MDR.
