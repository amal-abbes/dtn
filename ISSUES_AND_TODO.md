# 🛠 Issues & TODO List

## **🛑 Current Issues**
### **1️⃣ Storage Issues on Router**
**Problem:**  
- Router VM ran out of disk space, requiring expansion.
- This led to reconfigurations in MicroK8s and networking.

**Solution Implemented:**  
- Expanded disk space using `growpart` & `resize2fs`.
- Reinstalled MicroK8s and rejoined the cluster.

---

### **2️⃣ MetalLB Validation Failure**
**Problem:**  
- MetalLB webhook service failed (`connection refused` error).
- Caused delays in setting up Kubernetes LoadBalancer.

**Solution Implemented:**  
- Manually applied MetalLB address pool.
- Restarted MetalLB and verified IP allocation.

---

### **🚀 TODO Next Steps**


| Task | Status | Notes |
|------|--------|-------|
| Expand Router Storage | ✅ | Completed |
| Reinstall & Reconfigure MicroK8s | ✅ | Successfully rejoined cluster and all pods running |
| Setup Kubernetes Deployments | ⏳ | Pending uD3TN testing |
| Automate Network Testing (ping, tc, iperf) | ✅ | Implemented in simple scripts (introducing delays and ping tests) |
| Deploy uD3TN for DTN Simulation | ⏳ | Pending encountered some errors |
| Performance Tuning of Kubernetes Cluster | ⏳ | To be evaluated |
