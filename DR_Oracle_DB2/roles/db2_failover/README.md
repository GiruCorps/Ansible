Automatizacion de Ansible: Failover (Disaster Recovery) IBM Db2
======================================

## Descripcion del caso de uso
Este rol permite realizar failover de una instancia específica de IBM Db2 para bases de datos replicadas mediante HADR, desplegadas sobre AIX, en caso de una falla en la instancia ejecutándose en DCP.

## Resumen de pasos automatizados
1. Verifica el rol de la instancia en DCA (debería tener rol STANDBY).
2. Realiza el failover forzado.
3. Ejecuta comprobaciones posteriores al failover.
4. Verifica el rol de la(s) base(s) primaria(s).
5. Muestra posibles errores en caso de existir.

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
    - **Tipo**: string
    - **Required**: True

***Variables de inventario:***
* `ansible_host`: Corresponde a la dirección IP del servidor en el que se ejecuta IBM Db2, en IPv4
    - **Tipo**: string
    - **Values**: xxx.yyy.zzz.aaa
    - **Required**: true

***Variables de ejecución:***
* `instance`: Define el nombre de la instancia a la cual se va a afectar durante el failover
    - **Tipo**: string
    - **Required**: True

En el directorio inventories existe un inventario con un ejemplo para la creación del mismo.
