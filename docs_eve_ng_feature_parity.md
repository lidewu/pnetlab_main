# EVE-NG Feature Parity on PNETLab

This document maps common EVE-NG feature expectations to existing/implemented PNETLab capabilities in this repository, and defines the default Linux baseline as **Ubuntu 24.04**.

> Note: in this repository we can only change source defaults/templates and documentation. Runtime deployment settings still depend on your host image and installed packages.

## 1) Multi-vendor virtual labs
- **Status:** Supported.
- **Where:** QEMU, Docker, Dynamips, IOL, and VPCS device stacks are all present.
- **Implementation references:**
  - Core device abstractions and loaders.
  - Vendor templates under `templates/*.yml`.

## 2) Node and topology management APIs
- **Status:** Supported.
- **Where:** REST-style API endpoints for nodes, networks, labs, pictures, text objects, folders, and status.
- **Implementation references:** `includes/api_nodes.php`, `includes/api_networks.php`, `includes/api_labs.php`, `includes/api_topology.php`, `includes/api_status.php`, etc.

## 3) Templates and extensibility (add your own node types)
- **Status:** Supported.
- **Where:** YAML templates and PHP device handlers.
- **Implementation references:** `README.md`, `templates/device/*.yml`, `devices/*.php`.

## 4) Console access options
- **Status:** Supported.
- **Where:** Template schema includes Telnet, SSH, VNC, RDP, HTTP/HTTPS, WinBox options.
- **Implementation references:** `templates/device/qemu.yml`.

## 5) Saved lab artifacts and node parameters
- **Status:** Supported.
- **Where:** Per-node and per-lab model APIs plus parameter serialization in device layers.
- **Implementation references:** `includes/models/*.php`, `devices/functions.php`, `devices/device.php`.

## 6) Automation-friendly workflows
- **Status:** Supported.
- **Where:** API + config script fields + script timeout + exported config workflow.
- **Implementation references:** `templates/device/qemu.yml` and API modules.

## 7) Ubuntu default baseline
- **Status:** Implemented in this change.
- **What changed:** Linux-related default templates now use Ubuntu 24.04 profile (`templates/linux.yml` and `templates/newimage.yml`), including updated name/description, telnet console default, and Ubuntu-friendly qemu options.
- **Implementation references:** `templates/linux.yml`, `templates/newimage.yml`.

## 8) Operational recommendation
To fully align with your expected EVE-NG-like experience in production, deploy PNETLab on an Ubuntu 24.04 host and keep KVM/QEMU toolchain current.
