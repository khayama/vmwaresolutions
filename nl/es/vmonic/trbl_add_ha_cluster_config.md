---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# Problema de configuración de la consola de vSphere al añadir un clúster HA
{: #trbl_add_ha_cluster_config}

## Problema
{: #trbl_add_ha_cluster_config-problem}

Cuando se añade una configuración de clúster HA (alta disponibilidad) con una sola compartición de archivos, aparece el siguiente problema de configuración en los hosts ESXi:

> El número de almacenes de datos de latido para el host es 1, que es menor que el necesario: 2

## Solución
{: #trbl_add_ha_cluster_config-resolution}

Este problema se produce cuando no hay redundancia en el almacenamiento compartido para permitir el control de latido del almacén de datos.

Para obtener más información y ver los pasos a seguir para solucionar el problema, consulte [Error de HA: El número de almacenes de datos de latido para el host es 1, que es menor que el necesario: 2 (2004739)](https://kb.vmware.com/s/article/2004739).
