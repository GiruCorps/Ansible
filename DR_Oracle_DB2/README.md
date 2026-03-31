# Ansible Automation: IBM Db2 Disaster Recovery

Automation framework for managing disaster recovery operations on IBM Db2 using Ansible.  
Supports HADR-based replicated databases running on AIX across DCP and DCA environments.

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

## 🚀 Overview

This project provides automation for:

- Failover  
- Switchover  
- Switchback  
- Readiness validation  

Designed for IBM Db2 instances configured with **HADR (High Availability Disaster Recovery)** on **AIX**, across **DCP** and **DCA** environments.

---

## ⚙️ Automated Operations

### 🔴 Failover (Disaster Recovery)

1. Validates the role of the secondary instance  
2. Executes a forced failover  
3. Performs post-failover checks:
   - Database roles  
   - Log consistency  
4. Reports any detected errors  

---

### 🟡 Readiness

1. Validates instance roles (primary and standby)  
2. Scans for error/severe logs  
3. Confirms synchronization status of all databases  
4. Verifies:
   - Active synchronization  
   - Log consistency across sites  
5. Outputs a consolidated status report  

---

### 🔵 Switchback (DCA → DCP)

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

### 🟢 Switchover (DCP → DCA)

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

## 📋 Requirements

- Proper tagging must be applied for readiness execution depending on the target environment (**DCA** or **DCP**)  
- A connection user with privileges to switch to the Db2 administrative user  
- Python **2.7+** installed on the AIX server  

---

## 💡 Notes

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

# Automatización con Ansible: Disaster Recovery IBM Db2

Framework de automatización para gestionar operaciones de recuperación ante desastres en IBM Db2 utilizando Ansible.  
Soporta bases de datos replicadas con HADR ejecutándose sobre AIX en entornos DCP y DCA.

---

## 📌 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Operaciones Automatizadas](#operaciones-automatizadas)
  - [Failover (Disaster Recovery)](#failover-disaster-recovery)
  - [Readiness](#readiness)
  - [Switchback (DCA → DCP)](#switchback-dca--dcp)
  - [Switchover (DCP → DCA)](#switchover-dcp--dca)
- [Requisitos](#requisitos)
- [Licencia](#licencia)

---

## 🚀 Descripción General

Este proyecto permite automatizar:

- Failover  
- Switchover  
- Switchback  
- Validaciones de readiness  

Diseñado para instancias de IBM Db2 configuradas con **HADR (High Availability Disaster Recovery)** sobre **AIX**, en entornos **DCP** y **DCA**.

---

## ⚙️ Operaciones Automatizadas

### 🔴 Failover (Disaster Recovery)

1. Valida el rol de la instancia secundaria  
2. Ejecuta un failover forzado  
3. Realiza comprobaciones posteriores:
   - Roles de bases de datos  
   - Consistencia de logs  
4. Reporta errores detectados  

---

### 🟡 Readiness

1. Valida los roles de las instancias (primaria y standby)  
2. Busca logs de error/severe  
3. Confirma el estado de sincronización de todas las bases  
4. Verifica:
   - Sincronización activa  
   - Consistencia de logs entre sitios  
5. Muestra un reporte consolidado  

---

### 🔵 Switchback (DCA → DCP)

1. Valida los roles de las instancias  
2. Ejecuta comprobaciones previas:
   - Existencia y sincronización de logs  
   - Estado de sincronización de bases  
   - Estado de réplicas  
3. Ejecuta el switchback  
4. Realiza comprobaciones posteriores:
   - Logs de error/severe  
   - Roles de bases de datos  
5. Reporta errores encontrados  

---

### 🟢 Switchover (DCP → DCA)

1. Valida los roles de las instancias  
2. Ejecuta comprobaciones previas:
   - Existencia y sincronización de logs  
   - Estado de sincronización de bases  
   - Estado de réplicas  
3. Ejecuta el switchover  
4. Realiza comprobaciones posteriores:
   - Logs de error/severe  
   - Roles de bases de datos  
5. Reporta errores encontrados  

---

## 📋 Requisitos

- Uso de tags adecuados para ejecutar readiness según el entorno (**DCA** o **DCP**)  
- Usuario con privilegios para cambiar al usuario administrador de Db2  
- Python **2.7 o superior** instalado en el servidor AIX  

---

## 💡 Notas

- Diseñado para confiabilidad y repetibilidad  
- Reduce errores humanos en operaciones críticas  
- Garantiza consistencia en procesos de DR  

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas.  
Sigue el flujo estándar de GitHub:

1. Haz un fork del repositorio  
2. Crea una rama  
3. Envía un pull request  

---

## 📄 Licencia

Este proyecto está licenciado bajo la **GNU General Public License v3.0 (GPL-3.0)**.

Puedes:
- Usar  
- Modificar  
- Distribuir  

Bajo las siguientes condiciones:
- Los trabajos derivados deben mantenerse bajo GPL v3  
- El código fuente debe estar disponible al distribuir  

Consulta el archivo [LICENSE](./LICENSE) para más detalles.