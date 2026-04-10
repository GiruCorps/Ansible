# Automatización de Disaster Recovery IBM Db2 con Ansible

Framework de automatización end-to-end para gestionar **Disaster Recovery (DR) de IBM Db2** utilizando Ansible.

Diseñado para entornos con HADR sobre AIX, este proyecto transforma procesos de DR complejos y propensos a errores en **flujos confiables, repetibles y auditables**.

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

## 🎯 Valor del Proyecto

Este proyecto demuestra cómo:

- Automatizar operaciones críticas de DR en entornos distribuidos  
- Reducir el riesgo operativo durante escenarios de failover  
- Estandarizar procedimientos de recuperación entre equipos  
- Eliminar ejecuciones manuales propensas a errores  

> 💡 De intervención manual a automatización determinística.

## 🔥 Resultados clave

- Intervenciones manuales reducidas en operaciones de DR.
- Procesos de failover y switchover/switchback estandarizados.
- Tiempo de recuperación reducido y fiabilidad operacional.
- Error humano eliminado en escenarios críticos.

---

## 🧩 Arquitectura

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

## 🔄 Flujo de Disaster Recovery

Readiness → Switchover → Failover → Switchback


### 🟡 Readiness
Valida el estado del sistema antes de cualquier operación de DR:
- Roles de instancia  
- Consistencia de logs  
- Estado de sincronización  

---

### 🔵 Switchover
Transición controlada entre datacenters:
- DCP → DCA  
- Diseñado para escenarios sin pérdida de datos  

---

### 🔴 Failover
Procedimiento de recuperación ante fallas:
- Se ejecuta cuando DCP no está disponible  
- Promueve la instancia standby en DCA  

---

### 🟢 Switchback
Restauración de la topología original:
- DCA → DCP  
- Retorna el sistema a estado estable  

---

## ⚙️ Principios de Diseño

- **Ejecución idempotente** → seguro de re-ejecutar sin efectos secundarios  
- **Validación primero** → comprobaciones antes y después de cada operación  
- **Arquitectura modular** → roles independientes y reutilizables  
- **Lógica consciente del entorno** → soporte para contextos DCP y DCA  

---

## ⚙️ Requisitos

- IBM Db2 con **HADR configurado**  
- Entorno AIX  
- Python **2.7 o superior**  
- Ansible instalado  
- Acceso SSH con privilegios (`su`)  

---

## ▶️ Uso

### Validación de Readiness

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

## 🔥 Escenario de Ejemplo

El datacenter primario (DCP) deja de estar disponible:

1. Ejecutar validación de readiness
2. Disparar failover hacia DCA
3. Validar nuevo rol primario
4. Restaurar topología original con switchback cuando el sistema esté estable

---

## 💡 Beneficios Clave
* Reduce errores humanos en operaciones críticas
* Mejora el tiempo de recuperación (RTO)
* Garantiza ejecución consistente entre entornos
* Permite procesos de DR repetibles y auditables

---

## ⚠️ Notas Importantes
* Ejecutar siempre readiness antes de operaciones de DR
* Asegurar el entorno correcto (DCP/DCA)
* Validar en entornos no productivos antes de usar en producción

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