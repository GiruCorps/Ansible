# Ansible Db2 Disaster Recovery Automation

End-to-end automation framework for managing **IBM Db2 Disaster Recovery (DR)** using Ansible.

Built for HADR-based environments on AIX, this project transforms complex and error-prone DR procedures into **reliable, repeatable, and auditable workflows**.

---


## 📌 Table of Contents

- [Overview](#overview)
- [Automated Operations](#automated-operations)
  - [Failover (Disaster Recovery)](#failover-disaster-recovery)
  - [Readiness](#readiness)
  - [Switchback (DCA → DCP)](#switchback-dca--dcp)
  - [Switchover (DCP → DCA)](#switchover-dcp--dca)
- [Requirements](#requirements)
- [License](#license)

---

## 🎯 Project Value

This project demonstrates how to:

- Automate critical DR operations across distributed environments  
- Reduce operational risk during failover scenarios  
- Standardize recovery procedures across teams  
- Eliminate manual, error-prone execution  

> 💡 From manual intervention to deterministic automation.

## 🔥 Key Outcomes

- Reduced manual intervention in DR operations
- Standardized failover and switchover procedures
- Improved recovery time and operational reliability
- Eliminated human error in critical scenarios

## 🌎 Other Languages

- Spanish version available in [README.es.md](README.es.md)

---

## 🧩 Architecture

```
    .
    ├── inventories
    │  └── inventory
    ├── roles
    │  ├── db2_failover
    │  │  ├── tasks
    │  │  │  └── main.yml
    │  │  ├── vars
    │  │  │  └── main.yml
    │  │  └── README.md
    │  ├── db2_readiness
    │  │  ├── tasks
    │  │  │  ├── db2_readiness_DCA.yml
    │  │  │  ├── db2_readiness_DCP.yml
    │  │  │  └── main.yml
    │  │  ├── vars
    │  │  │  └── main.yml
    │  │  └── README.md
    │  ├── db2_switchback
    │  │  ├── tasks
    │  │  │  └── main.yml
    │  │  ├── vars
    │  │  │  └── main.yml
    │  │  └── README.md
    │  └── db2_switchover
    │     ├── tasks
    │     │  └── main.yml
    │     ├── vars
    │     │  └── main.yml
    │     └── README.md
    ├── ansible.cfg
    ├── failover.yml
    ├── LICENSE
    ├── readiness.yml
    ├── README.es.md
    ├── README.md
    ├── switchback.yml
    └── switchover.yml
```

---

## 🔄 Disaster Recovery Workflow

Readiness → Switchover → Failover → Switchback


### 🟡 Readiness
Validates system state before any DR operation:
- Instance roles  
- Log consistency  
- Synchronization status  

---

### 🔵 Switchover
Controlled transition between data centers:
- DCP → DCA  
- Designed for zero data loss scenarios  

---

### 🔴 Failover
Emergency recovery procedure:
- Triggered when DCP becomes unavailable  
- Promotes standby instance in DCA  

---

### 🟢 Switchback
Restores original topology:
- DCA → DCP  
- Returns system to steady-state operation  

---

## ⚙️ Design Principles

- **Idempotent execution** → Safe to re-run without side effects  
- **Validation-first approach** → Pre and post checks ensure consistency  
- **Modular architecture** → Independent, reusable roles  
- **Environment-aware logic** → Supports DCP and DCA contexts  

---

## ⚙️ Requirements

- IBM Db2 with **HADR configured**  
- AIX environment  
- Python **2.7+**  
- Ansible installed  
- SSH access with privilege escalation (`su`)  

---

## ▶️ Usage

### Readiness Check

```bash
ansible-playbook -i inventories/example/hosts.yml \
  playbooks/readiness.yml \
  -e "instance=db2inst1"
```

### Failover

```bash
ansible-playbook -i inventories/example/hosts.yml \
  playbooks/failover.yml \
  -e "instance=db2inst1"
```

### Switchover

```bash
ansible-playbook -i inventories/example/hosts.yml \
  playbooks/switchover.yml \
  -e "instance=db2inst1"
```

### Switchback

```bash
ansible-playbook -i inventories/example/hosts.yml \
  playbooks/switchback.yml \
  -e "instance=db2inst1"
```

---

## 🔥 Example Scenario

Primary data center (DCP) becomes unavailable:

1. Execute readiness validation
2. Trigger failover to DCA
3. Validate new primary role
4. Restore original topology with switchback once stable

---

## 💡 Key Benefits
* Reduces human error in critical operations
* Improves recovery time (RTO)
* Ensures consistent execution across environments
* Enables repeatable and auditable DR processes

---

## ⚠️ Important Notes
* Always execute readiness validation before DR operations
* Ensure correct environment targeting (DCP/DCA)
* Validate in non-production environments before rollout

---

## 🤝 Contributing

Contributions, improvements, and suggestions are welcome.  
Please follow standard GitHub workflow:

1. Fork the repository  
2. Create a feature branch  
3. Submit a pull request  

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)**.

You are free to:
- Use  
- Modify  
- Distribute  

Under the following conditions:
- Derivative works must also be licensed under GPL v3  
- Source code must be made available when distributing  

See the [LICENSE](./LICENSE) file for full details.