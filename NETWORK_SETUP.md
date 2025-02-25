# 🌐 Network Configuration

## 📌 Overview
This document details the network setup that I used. The **Router VM** acts as a gateway between **Ground (192.168.26.10)** and **Spacecraft (192.168.63.10)**, ensuring that all traffic passes through it.

## 📁 Network Configuration

| VM Name        | Interface  | IP Address       | Role |
|---------------|-----------|-----------------|------|
| **Router**     | `ens33`   | `192.168.32.141/24 (NAT)` | Internet Access |
|               | `br0`     | `192.168.26.1/24` | Bridge for Ground |
|               | `br0`     | `192.168.63.1/24` | Bridge for Space |
| **Ground**     | `ens37`   | `192.168.26.10/24` | Connected to Router |
| **Spacecraft** | `ens37`   | `192.168.63.10/24` | Connected to Router |

All Configured in /etc/netplan/50-cloud-init.yaml

## 🔄 Routing Table
```bash
ip route
```

---

## **📜 `VM_CONFIGURATION.md`**

## VMs Specifications

| VM Name   | vCPU | RAM  | Storage |
|-----------|------|------|---------|
| Router    | 2    | 6GB  |  default (extension needed) |
| Ground    | 2    | 6GB  |    (extension needed)|
| Spacecraft | 2    | 6GB  |  (extension needed)  |

## 🛠️ Installed Packages
- **Router VM**:
  - `net-tools`
  - `iptables`
  - `tcpdump`
  - `docker`
  - `kubernetes`
  - `tc (traffic control)`

- **Ground & Spacecraft VMs**:
  - `ping`
  - `iperf`
  - `net-tools`

## 🚀 Cloud-Init Configuration
Each VM is initialized with the following **Cloud-Init** configuration:
- **Image conversion**: Image Conversion:
Convert the Ubuntu cloud image to VMDK format for VMware compatibility:
```bash
cd ~/Cloud-Init-ISO
qemu-img convert -f qcow2 -O vmdk noble-server-cloudimg-amd64.img noble-server-cloudimg-amd64.vmdk
mv noble-server-cloudimg-amd64.vmdk /mnt/c/Users/amala/Documents/
```
- **Static IP assignments**
- **SSH access**
- **Network bridge on Router**
- **username:** ubuntu (for all 3 VMs) and common password
- **hostnames:** ground , space, router 
