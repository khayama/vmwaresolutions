---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas del release para V1.7
{: #relnotes_v17}

Este release incluye nuevas características, actualizaciones de componentes, mejoras en la usabilidad y correcciones de errores. Para ver una lista de los problemas solucionados en distintos releases, problemas conocidos del producto y sugerencias para utilizar {{site.data.keyword.vmwaresolutions_full}}, consulte [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Actualizaciones de instancias de VMware Cloud Foundation
{: #relnotes_v17-vcf}

Esta actualización se aplica a las siguientes actualizaciones y mejoras:
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Mejoras en la estabilidad del componente IBM CloudDriver
* La modalidad EVC (basada en el procesador Intel “Haswell” 2690-V3) se habilita en los despliegues de VMware preexistentes que están en los servidores V3 en el momento de la actualización.

  La modalidad EVC no está habilitada para los despliegues nuevos o existentes en servidores V4.
  {:note}

* Los despliegues de VMware Cloud Foundation desplegados antes del 22 de mayo y que por lo tanto utilizan servidores V3 solicitarán servidores V4 cuando se añada un nuevo nodo a la instancia. Estos servidores tienen 256 GB de memoria; si necesita 512 GB de memoria, después de añadir los servidores abra una incidencia de soporte para solicitar una actualización del servidor a 512 GB de memoria. Para obtener más información sobre cómo ponerse en contacto con el equipo de soporte de IBM, consulte [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

### Requisitos del proceso de actualización
{: #relnotes_v17-update-process}

En función de la complejidad del despliegue de la instancia de Cloud Foundation y de si tiene una configuración de varios sitios, es posible que el proceso de actualización requiera una secuencia de pasos que debe completar tal como se muestran en el separador **Actualización y parche** en la consola.

## Actualizaciones de instancias de VMware vCenter Server
{: #relnotes_v17-vcs}

### Soporte de clústeres
{: #relnotes_v17-cluster}

A partir del release V1.7, puede utilizar clústeres para gestionar servidores ESXi en instancias de vCenter Server para mejorar la gestión de recursos y la alta disponibilidad. Los servidores ESXi que ha configurado al solicitar una instancia se agrupan como **cluster1** de forma predeterminada. Puede ver los detalles del clúster o añadir hasta un total de cinco clústeres a una instancia desde el nuevo separador **Infraestructura** de la página de detalles de la instancia. Cuando amplíe o reduzca la capacidad de una instancia, puede seleccionar el clúster al que se van a añadir los servidores ESXi o del que se van a eliminar los servidores ESXi. Para obtener más información, consulte [Adición, visualización y supresión de clústeres para instancias de vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

### Mejoras en el despliegue de la recuperación tras desastre de Zerto
{: #relnotes_v17-zerto}

El despliegue del servicio de recuperación tras error de Zerto se ha automatizado y se gestiona a través de una incidencia de soporte. Todos los componentes Zerto, como por ejemplo una subred privada portátil, una VSI (instancia de servicio virtual) de Windows y los cargos de licencia de Zerto, aparecen listados en el coste estimado, de modo que los puede revisar antes de realizar el pedido. Para obtener más información, consulte [Proceso de despliegue de la recuperación tras desastre de Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

### Funciones de actualización de licencias de NSX
{: #relnotes_v17-nsx}

Puede actualizar la edición de su licencia de NSX desde el separador **Resumen** de la instancia de vCenter Server. La actualización de licencia sustituye todas las licencias existentes de NSX SoftLayer en la cuenta por la nueva instancia. Para obtener más información, consulte [Visualización de instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances).

## Mejoras en la usabilidad
{: #relnotes_v17-ui}

Se han realizado mejoras en la interfaz de usuario:
* Se ha cambiado el nombre del separador **Propiedades** de la página de detalles de la instancia de Cloud Foundation por **Resumen**. Ahora puede ver los detalles de la instancia, la información de acceso de los componentes relacionados con la instancia y el historial de despliegues en este separador.
* Se ha incorporado un nuevo separador **Infraestructura** en la página de detalles de la instancia de Cloud Foundation. Puede ver, añadir o eliminar servidores ESXi en este separador.
* La documentación de {{site.data.keyword.vmwaresolutions_short}} tiene un nuevo formato y ahora está completamente integrada en el catálogo de Bluemix, junto con el conjunto de documentación de Bluemix. Puede acceder a la documentación de una de las siguientes formas:
  * Desde {{site.data.keyword.vmwaresolutions_short}}, pulse **Docs** a la izquierda de la cabecera.
  * Desde el catálogo de documentación de Bluemix, desplácese hacia abajo hasta la sección **Cálculo y servicios** y pulse **{{site.data.keyword.vmwaresolutions_short}}**.
