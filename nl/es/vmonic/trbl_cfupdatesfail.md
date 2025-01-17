---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Las actualizaciones de instancias de Cloud Foundation fallan si la operación de los servidores ESXi falla
{: #trbl_cfupdatesfail}

## Problema
{: #trbl_cfupdatesfail-problem}

Si añade servidores ESXi a una instancia de la V1.5 o la V1.6 de VMware Cloud Foundation y la operación de adición falla, la opción de actualización se inhabilita y no puede aplicar la actualización V1.5 a la V1.6 ni la actualización V1.6 a la V1.7 a la instancia.

## Solución
{: #trbl_cfupdatesfail-resolution}

Antes de aplicar la actualización V1.6 a una instancia de Cloud Foundation V1.5, o la actualización V1.7 a una instancia de V1.6, asegúrese de que la operación de añadir servidores ESXi se ha realizado correctamente.
