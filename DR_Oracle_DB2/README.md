# Ansible Automation: IBM Db2 Disaster Recovery

Automation framework for managing disaster recovery operations on IBM Db2 using Ansible.  
Supports HADR-based replicated databases running on AIX across DCP and DCA environments.

## 🎯 Project Value

This project demonstrates how to automate end-to-end disaster recovery for IBM Db2 environments using Ansible.

### 🔥 Key Outcomes

- Reduced manual intervention in DR operations
- Standardized failover and switchover procedures
- Improved recovery time and operational reliability
- Eliminated human error in critical scenarios

## 🌎 Other Languages

- Spanish version available in [README.es.md](README.es.md)

---

## 📌 Table of Contents

- [Overview](#overview)
- [Automated Operations](#automated-operations)
  - [Failover (Disaster Recovery)](#failover-disaster-recovery)
  - [Readiness](#readiness)
  - [Switchback (DCA → DCP)](#switchback-dca--dcp)
  - [Switchover (DCP → DCA)](#switchover-dcp--dca)
- [Requirements](#requirements)
- [Notes](#notes)
- [License](#license)

---

## <a id="overview"></a> 🚀 Overview

This project provides automation for:

- Failover  
- Switchover  
- Switchback  
- Readiness validation  

Designed for IBM Db2 instances configured with **HADR (High Availability Disaster Recovery)** on **AIX**, across **DCP** and **DCA** environments.

---

## <a id="automated-operations"></a>⚙️ Automated Operations

### <a id="failover-disaster-recovery"></a>🔴 Failover (Disaster Recovery)

1. Validates the role of the secondary instance  
2. Executes a forced failover  
3. Performs post-failover checks:
   - Database roles  
   - Log consistency  
4. Reports any detected errors  

---

### <a id="readiness"></a>🟡 Readiness

1. Validates instance roles (primary and standby)  
2. Scans for error/severe logs  
3. Confirms synchronization status of all databases  
4. Verifies:
   - Active synchronization  
   - Log consistency across sites  
5. Outputs a consolidated status report  

---

### <a id="switchback-dca--dcp"></a>🔵 Switchback (DCA → DCP)

1. Validates instance roles  
2. Performs pre-checks:
   - Log availability and synchronization  
   - Database synchronization status  
   - Replica health  
3. Executes switchback  
4. Performs post-checks:
   - Error/severe logs  
   - Database roles  
5. Reports any issues detected  

---

### <a id="switchover-dcp--dca"></a>🟢 Switchover (DCP → DCA)

1. Validates instance roles  
2. Performs pre-checks:
   - Log availability and synchronization  
   - Database synchronization status  
   - Replica health  
3. Executes switchover  
4. Performs post-checks:
   - Error/severe logs  
   - Database roles  
5. Reports any issues detected  

---

## <a id="requirements"></a>📋 Requirements

- Proper tagging must be applied for readiness execution depending on the target environment (**DCA** or **DCP**)  
- A connection user with privileges to switch to the Db2 administrative user  
- Python **2.7+** installed on the AIX server  

---

## <a id="notes"></a>💡 Notes
- Always execute readiness validation before DR operations
- Ensure correct environment targeting (DCP/DCA)
- Designed for reliability and repeatability  
- Reduces human error during critical operations  
- Ensures consistent execution of DR procedures  

---

## 🤝 Contributing

Contributions, improvements, and suggestions are welcome.  
Please follow standard GitHub workflow:

1. Fork the repository  
2. Create a feature branch  
3. Submit a pull request  

---

## <a id="readiness"></a>📄 License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

You are free to:
- Use  
- Modify  
- Distribute  

Under the following conditions:
- Derivative works must also be licensed under GPL v3  
- Source code must be made available when distributing  

See the [LICENSE](./LICENSE) file for full details.