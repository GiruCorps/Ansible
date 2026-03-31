Automatizacion de Ansible: Switchover IBM Db2 HADR
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
