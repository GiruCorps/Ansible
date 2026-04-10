# Ansible Automation: IBM Db2 HADR Switchback

Automation role for performing controlled switchback operations on IBM Db2 instances using Ansible.  
Designed for HADR-replicated databases running on AIX, moving workloads from DCA to DCP.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Automated Workflow](#automated-workflow)
- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [License](#license)

---

## 🚀 Overview

This role enables controlled **switchback operations** for IBM Db2 instances configured with:

- **HADR (High Availability Disaster Recovery)**
- **AIX environments**
- **DCA → DCP transition**

It ensures a safe and validated transition of database roles between standby and primary nodes.

---

## ⚙️ Automated Workflow

1. Validates instance roles (primary and standby)  
2. Performs pre-switchback checks:
   - Log availability and synchronization  
   - Database synchronization status  
   - Replica health  
3. Executes the switchback  
4. Performs post-switchback checks:
   - Generated `error`/`severe` logs  
   - Active database roles  
5. Reports any detected issues  

---

## 📋 Requirements

- A connection user with privileges to switch (`su`) to the Db2 administrative user  
- Python **2.7+** installed on the AIX server  

---

## ⚙️ Role Variables

> ⚠️ Note: Most variables are defined in `vars/main.yml`

### 🔹 Group Variables

- `usuario`  
  - Description: Db2 instance administrative user (typically matches the instance name)  
  - Type: `string`  
  - Required: **true**

---

### 🔹 Inventory Variables

- `ansible_host`  
  - Description: Target server IP address (IPv4) where IBM Db2 is running  
  - Type: `string`  
  - Format: `xxx.yyy.zzz.aaa`  
  - Required: **true**

---

### 🔹 Execution Variables

- `instance`  
  - Description: Name of the Db2 instance affected during the switchback  
  - Type: `string`  
  - Required: **true**

---

## 💡 Notes

- Designed for safe and repeatable operations  
- Minimizes operational risk  
- Ensures validation before and after execution  

---

## 🤝 Contributing

Contributions are welcome:

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

# Automatización con Ansible: Switchback IBM Db2 HADR

Rol de automatización para ejecutar operaciones de switchback controlado en instancias de IBM Db2 utilizando Ansible.  
Diseñado para bases de datos replicadas con HADR sobre AIX, realizando el cambio de DCA hacia DCP.

---

## 📌 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Flujo Automatizado](#flujo-automatizado)
- [Requisitos](#requisitos)
- [Variables del Rol](#variables-del-rol)
- [Licencia](#licencia)

---

## 🚀 Descripción General

Este rol permite ejecutar **operaciones de switchback controlado** para instancias de IBM Db2 configuradas con:

- **HADR (High Availability Disaster Recovery)**  
- **Entornos AIX**  
- **Transición DCA → DCP**  

Garantiza una transición segura y validada entre nodos standby y primario.

---

## ⚙️ Flujo Automatizado

1. Valida los roles de las instancias (primaria y standby)  
2. Ejecuta comprobaciones previas:
   - Existencia y sincronización de logs  
   - Estado de sincronización de las bases  
   - Estado de las réplicas  
3. Realiza el switchback  
4. Ejecuta comprobaciones posteriores:
   - Logs `error`/`severe` generados  
   - Roles de las bases de datos  
5. Reporta errores detectados  

---

## 📋 Requisitos

- Usuario con privilegios para ejecutar `su` hacia el usuario administrador de Db2  
- Python **2.7 o superior** instalado en el servidor AIX  

---

## ⚙️ Variables del Rol

> ⚠️ Nota: La mayoría de variables están definidas en `vars/main.yml`

### 🔹 Variables de grupo

- `usuario`  
  - Descripción: Usuario administrador de la instancia Db2  
  - Tipo: `string`  
  - Requerido: **true**

---

### 🔹 Variables de inventario

- `ansible_host`  
  - Descripción: Dirección IP del servidor donde se ejecuta IBM Db2  
  - Tipo: `string`  
  - Formato: `xxx.yyy.zzz.aaa`  
  - Requerido: **true**

---

### 🔹 Variables de ejecución

- `instance`  
  - Descripción: Nombre de la instancia afectada durante el switchback  
  - Tipo: `string`  
  - Requerido: **true**

---

## 💡 Notas

- Diseñado para operaciones seguras y repetibles  
- Reduce riesgos operativos  
- Garantiza validaciones antes y después de la ejecución  

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas:

1. Realiza un fork  
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