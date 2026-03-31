Automatizacion de Ansible: Comprobación de readiness IBM Db2
======================================

## Descripcion del caso de uso
Este rol permite realizar una comprobación del eestado de readiness (factibilidad de movimiento de un datacenter a otro) de una instancia específica de IBM Db2 para bases de datos replicadas mediante HADR, desplegadas sobre AIX. El rol incluye dos secciones definidas por diferentes `tags`, tanto para ejecución en DCA como en DCP.

## Resumen de pasos automatizados
1. Verifica los roles de las instancias (primaria y standby).
2. Busca logs de `error`/`severe` en la instancia de base de datos.
3. Confirma la sincronización de cada una de las bases presentes en la instancia.
4. Verifica que la sincronización se esté realizando y que los logs se mantengan iguales en ambos sitios.
5. Muestra las novedades en un mensaje final.

## Requisitos
Este rol requiere:
  - Para una correcta ejecución, se debe incluir el tag necesario para ejecución, ya sea en `DCA` o en `DCP`.
  - Python versión 2.7 o superior instalado en el execution environment.

## Variables de rol
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
* `instance`: Define el nombre de la instancia a la cual se va a verificar la factibilidad de movimiento. Para esta comprobación, se puede utilizar el nombre de instancia `all`, el cual realizará la verificación en todos los servidores de los grupos primario (`dcp`) y secundario (`dca`).
    - **Tipo**: string
    - **Required**: True

***Tags de ejecucíon:***
* `db2_readiness_DCP`: Ejecuta las tareas de verificación en una instancia cuyo rol primario está actualmente en DCP.
* `db2_readiness_DCA`: Ejecuta las tareas de verificación en una instancia cuyo rol primario está actualmente en DCA.
