
**Ansible Automation: IBM Db2 Disaster Recovery**
======================================

## **Use Case Description**  

This collection enables performing switchover, switchback, failover, and readiness checks for a specific IBM Db2 instance. It is designed for databases replicated using HADR and deployed on AIX, across both DCP and DCA environments.  

## **Summary of Automated Steps**  

### *Failover (Disaster Recovery)*  

1. Verifies the roles of the secondary instance.  
2. Executes a forced failover.  
3. Performs post-failover validations (database roles and logs).  
4. Displays any detected errors, if present.  

### *Readiness*  

1. Verifies the roles of the instances (primary and standby).  
2. Searches for error/severe logs in the database instance.  
3. Confirms synchronization status for each database within the instance.  
4. Verifies that synchronization is active and that logs remain consistent across both sites.  
5. Displays a summary of findings in a final message.  

### *Switchback (DCA to DCP)*  

1. Verifies the roles of the instances (primary and standby).  
2. Performs pre-switchback validations: log availability and synchronization, database synchronization status, and replica status.  
3. Executes the switchback operation.  
4. Performs post-switchback validations: generated error/severe logs and roles of running databases within the instance.  
5. Reports any errors encountered during the process.  

### *Switchover (DCP to DCA)*  

1. Verifies the roles of the instances (primary and standby).  
2. Performs pre-switchover validations: log availability and synchronization, database synchronization status, and replica status.  
3. Executes the switchover operation.  
4. Performs post-switchover validations: generated error/severe logs and roles of running databases within the instance.  
5. Reports any errors encountered during the process.  

## **Requirements**  

These roles require:  
- For proper execution of the readiness role, the appropriate tag must be included depending on the target environment (DCA or DCP).  
- A connection user with sufficient privileges to switch to the database administrator user.  
- Python version 2.7 or higher installed on the AIX server.  


**Automatizacion de Ansible: Switchover IBM Db2 HADR**
======================================

## Descripcion del caso de uso
Este rol permite realizar un Switchover (movimiento controlado) de una instancia específica de IBM Db2 para bases de datos replicadas mediante HADR, desplegadas sobre AIX, desde DCP hacia DCA.

## Resumen de pasos automatizados
1. Verifica los roles de las instancias (primaria y standby).
2. Ejecuta comprobaciones previas al switchover: existencia y sincronización de logs, estado de la sincronización de las bases, estado de la(s) réplica(s).
3. Realiza el switchover.
4. Ejecuta comprobaciones posteriores al switchover: logs de `error`/`severe` generados, roles de las bases de datos en ejecución en la instancia.
5. Presenta los posibles errores encontrados durante el proceso.

## Requisitos
Este rol requiere:
  - Usuario de conexión con privilegios para realizar `su` hacia el usuario administrador de la base de datos.
  - Python versión 2.7 o superior instalado en el servidor AIX.

## Variables de rol
*Pendiente de actualización*

El rol define la mayoría de sus variables en `vars/main.yml`.
Las variables adicionales son las siguientes:

***Variables de grupo:***
* `usuario`: Contiene el nombre del usuario administrador de la instancia Db2 (usualmente el mismo nombre de la instancia)
    - **Tipo**: stringP
    - **Required**: True

***Variables de inventario:***
* `ansible_host`: Corresponde a la dirección IP del servidor en el que se ejecuta IBM Db2, en IPv4
    - **Tipo**: string
    - **Values**: xxx.yyy.zzz.aaa
    - **Required**: true

***Variables de ejecución:***
* `instance`: Define el nombre de la instancia a la cual se va a afectar durante el switchover
    - **Tipo**: string
    - **Required**: True
