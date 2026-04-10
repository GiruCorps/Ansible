# Ansible Automation: IBM Db2 Readiness Validation

Automation role for validating the readiness state of IBM Db2 instances using Ansible.  
Designed for HADR-replicated databases running on AIX, ensuring safe conditions for data center transitions between DCP and DCA.

---

## 📌 Table of Contents

- [Overview](#overview)
- [Automated Workflow](#automated-workflow)
- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Execution Tags](#execution-tags)
- [License](#license)

---

## 🚀 Overview

This role performs **readiness validation** to determine whether a Db2 instance is in a safe state to:

- Move workloads between data centers  
- Execute switchover or failover operations  

It supports execution in both **DCP** and **DCA** environments using dedicated tags.

---

## ⚙️ Automated Workflow

1. Validates instance roles (primary and standby)  
2. Scans for `error`/`severe` logs in the database instance  
3. Confirms synchronization status of all databases  
4. Verifies:
   - Active synchronization  
   - Log consistency across both sites  
5. Outputs a summary of findings  

---

## 📋 Requirements

- Proper execution requires selecting the appropriate tag:
  - `DCP` or `DCA`  
- Python **2.7+** installed in the execution environment  

---

## ⚙️ Role Variables

> ⚠️ Most variables are defined in `vars/main.yml`

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
  - Description: Db2 instance name to validate  
  - Special value: `all` → validates all instances across primary (`dcp`) and secondary (`dca`) groups  
  - Type: `string`  
  - Required: **true**

---

## 🏷️ Execution Tags

- `db2_readiness_DCP`  
  Executes validation for instances where the primary role is currently in **DCP**

- `db2_readiness_DCA`  
  Executes validation for instances where the primary role is currently in **DCA**

---

## 💡 Notes

- Designed as a prerequisite validation step before DR operations  
- Helps prevent unsafe transitions between environments  
- Provides visibility into synchronization and system health  

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


# Automatización con Ansible: Validación de Readiness IBM Db2

Rol de automatización para validar el estado de readiness de instancias IBM Db2 utilizando Ansible.  
Diseñado para bases de datos replicadas con HADR sobre AIX, asegurando condiciones seguras para movimientos entre DCP y DCA.

---

## 📌 Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Flujo Automatizado](#flujo-automatizado)
- [Requisitos](#requisitos)
- [Variables del Rol](#variables-del-rol)
- [Tags de Ejecución](#tags-de-ejecución)
- [Licencia](#licencia)

---

## 🚀 Descripción General

Este rol permite realizar una **validación de readiness** para determinar si una instancia Db2 está en condiciones seguras para:

- Mover cargas entre datacenters  
- Ejecutar operaciones de switchover o failover  

Soporta ejecución en entornos **DCP** y **DCA** mediante el uso de tags específicos.

---

## ⚙️ Flujo Automatizado

1. Valida los roles de las instancias (primaria y standby)  
2. Busca logs de `error`/`severe` en la instancia  
3. Confirma la sincronización de todas las bases de datos  
4. Verifica:
   - Sincronización activa  
   - Consistencia de logs entre ambos sitios  
5. Muestra un resumen de resultados  

---

## 📋 Requisitos

- Se debe seleccionar el tag adecuado para la ejecución:
  - `DCP` o `DCA`  
- Python **2.7 o superior** en el entorno de ejecución  

---

## ⚙️ Variables del Rol

> ⚠️ La mayoría de variables están definidas en `vars/main.yml`

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
  - Descripción: Nombre de la instancia a validar  
  - Valor especial: `all` → valida todas las instancias en grupos primario (`dcp`) y secundario (`dca`)  
  - Tipo: `string`  
  - Requerido: **true**

---

## 🏷️ Tags de ejecución

- `db2_readiness_DCP`  
  Ejecuta validación para instancias cuyo rol primario está en **DCP**

- `db2_readiness_DCA`  
  Ejecuta validación para instancias cuyo rol primario está en **DCA**

---

## 💡 Notas

- Diseñado como validación previa a operaciones de DR  
- Previene transiciones inseguras entre entornos  
- Proporciona visibilidad sobre sincronización y estado del sistema  

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