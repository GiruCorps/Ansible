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
