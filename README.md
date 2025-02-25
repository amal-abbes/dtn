#  VM Setup & Networking

This repository contains the **current state of the VM setup, network configuration, automated testing, and Kubernetes deployment** from the master thesis with future intended steps.

## 📌 Overview
- **Goal**: Implement a delay- and interruption-tolerant cloud infrastructure for space applications.
- **Current Progress**:
  - ✅ **VM Communication**: Ground and Spacecraft communicate via Router.
  - ✅ **Network bridge configured on Router** (ens37 + ens38 → br0).
  - ✅ **NAT enabled** for Ground & Spacecraft via Router.
  - ✅ **Traffic control (`tc`) applied** for simulating delays & loss.
  - ✅ **Automated ping testing script** deployed.
  - ✅ **Docker & Kubernetes installed for container orchestration**.
  - ⏳ **uDTN implementation and monitoring tools are pending due to storage issues**.

## 📁 Repository Contents
| File                  | Description |
|-----------------------|-------------|
| `NETWORK_SETUP.md`     | Detailed network configuration |
| `VM_CONFIGURATION.md`  | VM setup details (Cloud-Init, disk space, etc.) |
| `TEST_RESULTS.md`      | Results of network tests (ping, TCPDump logs) |
| `ISSUES_AND_TODO.md`   | Issues encountered and next steps |
| `FUTURE_WORK.md`       | Future improvements & optimizations |
| `scripts/`            | Automation scripts (networking, testing, etc.) |
| `configs/`            | Netplan configuration files for VMs |
| `kubernetes/`         | Kubernetes deployment manifests |

## 🚀 Next Steps
- **Deploy & validate uDTN** implementation.
- **Performance tuning & scalability tests** in Kubernetes.
- **Optimize network parameters** to improve delay-tolerant communication.

---
**Author:** Amal Abbes  
**Date:** February 2025
