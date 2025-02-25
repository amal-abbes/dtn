# **DARKSOL Documentation Update**

## **Storage Issue & Router Reconfiguration**

### **Issue Encountered**
During the setup of the Kubernetes cluster, a **storage issue** was encountered on the **Router VM**. The disk space was insufficient, requiring an **expansion of storage** and subsequent reconfiguration of the router.

### **Solution Implemented**
1. **Expanding Storage**:
   - Increased the allocated disk space for the router VM.
   - Applied changes and resized the filesystem.

2. **Reconfiguring Router VM**:
   - Reapplied network settings.
   - Reinstalled MicroK8s and rejoined the cluster.
   - Reconfigured MetalLB and network components.

---

## **Steps Taken**

### **1. Expanding Storage**
After expanding the VM disk space in VMware Workstation:

```sh
# Check available disk space before expansion
lsblk

# Identify the partition to expand (e.g., /dev/sda3)
sudo growpart /dev/sda 3

# Resize the filesystem
sudo resize2fs /dev/sda3

# Verify the new space allocation
df -h
```

---

### **2. Router Reconfiguration**

#### **Reapplying Network Settings**
```sh
# Verify network interfaces
ip a

# Reconfigure Netplan (example configuration in /etc/netplan/50-cloud-init.yaml)
sudo nano /etc/netplan/50-cloud-init.yaml
```

Example Netplan Configuration:
```yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: true
    ens37:
      addresses:
        - 192.168.26.1/24
    ens38:
      addresses:
        - 192.168.63.1/24
  bridges:
    br0:
      interfaces: [ens37, ens38]
      addresses:
        - 192.168.26.1/24
        - 192.168.63.1/24
      parameters:
        stp: false
        forward-delay: 0
```

```sh
# Apply Netplan changes
sudo netplan apply
```

---

#### **Reinstalling MicroK8s & Rejoining Cluster**
```sh
# Remove previous installation
sudo snap remove microk8s

# Reinstall MicroK8s
sudo snap install microk8s --classic

# Join the cluster again
microk8s join 192.168.32.141:25000/<cluster-token>
```

---

#### **Reconfiguring MetalLB**
```sh
# Enable MetalLB
microk8s enable metallb

# Assign IP range for MetalLB (adapt to setup)
192.168.26.100-192.168.26.150,192.168.32.200-192.168.32.220,192.168.63.200-192.168.63.250
```

---

### **Outcome**
- **Storage expanded successfully**
- **Router VM reconfigured and rejoined the cluster**
- **MicroK8s and MetalLB operational**

---

### **Next Steps**
- Proceed with deploying **uD3TN** and other components.
- Validate **network connectivity and routing**.
- Continue Kubernetes cluster setup per **Master's Thesis specifications**.
