
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

**Automatizacion de Ansible: Disaster Recovery IBM Db2**
======================================

## **Descripcion del caso de uso**  

Esta colección permite realizar un switchover, switchback, failover y comprobación de readiness de una instancia específica de IBM Db2 para bases de datos replicadas mediante HADR, desplegadas sobre AIX, tanto en DCP como en DCA.  

## **Resumen de pasos automatizados**  

### *Failover (Disaster Recovery)*  

1. Verifica los roles de la instancia secundaria.  
2. Realiza el failover forzado.  
3. Ejecuta comprobaciones posteriores al failover (roles de las bases y logs).  
4. Muestra posibles errores en caso de existir.  

### *Readiness*  

1. Verifica los roles de las instancias (primaria y standby).  
2. Busca logs de error/severe en la instancia de base de datos.  
3. Confirma la sincronización de cada una de las bases presentes en la instancia.  
4. Verifica que la sincronización se esté realizando y que los logs se mantengan iguales en ambos sitios.  
5. Muestra las novedades en un mensaje final.  

### *Switchback (DCA a DCP)*  

1. Verifica los roles de las instancias (primaria y standby).  
2. Ejecuta comprobaciones previas al switchback: existencia y sincronización de logs, estado de la sincronización de las bases, estado de la(s) réplica(s).  
3. Realiza el switchback.  
4. Ejecuta comprobaciones posteriores al switchback: logs de error/severe generados, roles de las bases de datos en ejecución en la instancia.  
5. Presenta los posibles errores encontrados durante el proceso.  

### *Switchover (DCP a DCA)*  

1. Verifica los roles de las instancias (primaria y standby).  
2. Ejecuta comprobaciones previas al switchover: existencia y sincronización de logs, estado de la sincronización de las bases, estado de la(s) réplica(s).  
3. Realiza el switchover.  
4. Ejecuta comprobaciones posteriores al switchover: logs de error/severe generados, roles de las bases de datos en ejecución en la instancia.  
5. Presenta los posibles errores encontrados durante el proceso.  

## **Requisitos**  

Estos roles requieren:  
- Para una correcta ejecución del rol de readiness, se debe incluir el tag necesario para ejecución, ya sea en DCA o en DCP.  
- Usuario de conexión con privilegios para realizar su hacia el usuario administrador de la base de datos.  
- Python versión 2.7 o superior instalado en el servidor AIX.  
