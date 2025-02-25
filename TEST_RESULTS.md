# 📊 Test Results & Validation

## **📌 Overview**
This document contains the results of various network and performance tests conducted on the DARKSOL environment.

## **✅ Ping Test**
### **Goal**: Verify connectivity between Ground, Spacecraft, and Router.

```bash
# From Ground VM
ping -c 5 192.168.63.10  # Ping Spacecraft
ping -c 5 192.168.26.1   # Ping Router

# From Spacecraft VM
ping -c 5 192.168.26.10  # Ping Ground
ping -c 5 192.168.63.1   # Ping Router
```

### **Results**
| Source  | Destination | Success (%) | Latency (ms) |
|---------|------------|-------------|--------------|
| Ground  | Spacecraft | 100%        | ~ ms       |
| Spacecraft | Ground | 100%        | ~ ms       |

---

## **📊 TCPDump Analysis**
### **Goal**: Capture network packets to analyze data flow.
```bash
# On Router VM
sudo tcpdump -i br0 -w network_traffic.pcap
```

### **Observations**
- **ICMP Requests & Replies** captured.
- **No packet loss** between nodes.
- **NAT verification successful**.

---

## **📉 Traffic Control (`tc`) Tests**
### **Goal**: Simulate network delay & packet loss.

#### **Delay Simulation**
```bash
# On Router VM
sudo tc qdisc add dev br0 root netem delay 300ms
```
**Result:** Ground-to-Spacecraft communication experienced an **average latency increase of 300ms**.

#### **Packet Loss Simulation**
```bash
# On Router VM
sudo tc qdisc change dev br0 root netem loss 10%
```
**Result:** Approximately **10% of packets dropped**, as expected.

---

## **🛠 Next Steps**
- Automate network testing.
- Integrate `tc` rules dynamically based on scenario conditions.
- Optimize Kubernetes deployment for delay-tolerant applications.
- Monitoring Tools.
