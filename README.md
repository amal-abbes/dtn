
# DARKSOL VM Setup & Networking

This repository contains the current state of the VM setup and network configuration for the DARKSOL project at TU Dresden.

## 📌 Overview
- **Goal**: Implement a delay- and interruption-tolerant cloud infrastructure for space applications.
- **Current Progress**:
  - ✅ Ground and Spacecraft VMs can communicate via the Router.
  - ✅ Network bridge configured on Router (ens37 + ens38 → br0).
  - ✅ NAT enabled for Ground & Spacecraft to access the Internet via Router.
  - ✅ Traffic control (`tc`) applied to simulate network delays and loss.

## 📁 Repository Contents
| File                  | Description |
|-----------------------|-------------|
| `NETWORK_SETUP.md`     | Detailed network configuration |
| `VM_CONFIGURATION.md`  | VM setup details (cloud-init, disk space, etc.) |
| `TEST_RESULTS.md`      | Results of network tests (ping, TCPDump logs) |
| `ISSUES_AND_TODO.md`   | Issues encountered and next steps |
| `scripts/`            | Automation scripts (networking, traffic shaping, etc.) |
| `configs/`            | Netplan configuration files for VMs |

## 🚀 Next Steps
- Final validation of NAT and routing setup.
- Deployment of containerized applications (Kubernetes).
- Performance testing under simulated delays.

---
**Author:** Amal Abbes  
**Date:** February 2025
