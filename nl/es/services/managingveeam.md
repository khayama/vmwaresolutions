---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

# Gestión de Veeam on IBM Cloud
{: #managingveeam}

Después de desplegar el servicio en la instancia, puede acceder a la consola de Veeam utilizando RDP para gestionar la copia de seguridad y restauración de todas las máquinas virtuales del entorno, incluida la copia de seguridad y la restauración de los componentes de gestión. También puede actualizar el servicio descargando e instalando las actualizaciones de Veeam desde el sitio web de Veeam.

Para las instancias que se han desplegado en releases anteriores a V1.8, si desea utilizar el servicio Veeam on {{site.data.keyword.cloud}}, debe sustituir la VSI de Veeam existente en las instancias. Para obtener más información, consulte la sección _Sustitución de la VSI de Veeam de instancias anteriores a V1.8 con Veeam on IBM Cloud_.

## Acceso a la consola de Veeam mediante RDP
{: #managingveeam-accessing}

Para gestionar el servicio Veeam on {{site.data.keyword.cloud_notm}}, acceda a la consola de Veeam siguiendo estos pasos:
1. Utilice Remote Desktop Protocol (RDP) para conectar con la dirección IP de Windows.
2. Inicie una sesión en la consola de Windows utilizando las credenciales del administrador.
3. Acceda a la consola de Veeam desde la consola de Windows utilizando las credenciales del administrador.

Puede encontrar la dirección IP de Windows y las credenciales del administrador en el servicio Veeam en la página de detalles del servicio de {{site.data.keyword.cloud_notm}}.

Para obtener más información, consulte [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Copia de seguridad y restauración de componentes de gestión para instancias que tienen instalado Veeam on IBM Cloud
{: #managing-veeam-backup-and-replication}

El servicio de Veeam on {{site.data.keyword.cloud_notm}} se puede configurar para hacer copia de seguridad de los componentes de gestión mediante la consola de Veeam. Para obtener más información, consulte [Copia de seguridad de componentes](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

Para instancias que se han desplegado en (o se han actualizado a) V1.8 y releases posteriores, no se hará copia de seguridad automática de los cambios de configuración a su entorno. Por lo tanto, antes de modificar la configuración de su entorno, se recomienda que realice una copia de seguridad manual de los componentes de gestión ejecutando el trabajo de copia de seguridad de gestión en la consola de Veeam. Para obtener más información sobre cómo realizar copias de seguridad manualmente, consulte las [Instrucciones técnicas de Veeam](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

Si se producen errores en los componentes de gestión, puede restaurar dichos componentes a una copia de seguridad anterior mediante la consola de Veeam. Para obtener más información sobre cómo restaurar copias de seguridad manualmente, consulte las [Instrucciones técnicas de Veeam]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Aplicación de actualizaciones de Veeam on IBM Cloud
{: #managingveeam-updates}

El usuario es el responsable de mantener el software Veeam actualizado al nivel de la versión más reciente.

### Aplicación de actualizaciones para las instancias desplegadas con red pública y privada
{: #managingveeam-updates-public-private}

Si el servicio Veeam está instalado en una instancia con red pública y privada, puede comprobar si hay actualizaciones y descargarlas mediante el propio software Veeam.

### Aplicación de actualizaciones para las instancias desplegadas solo con red privada
{: #managingveeam-updates-private}

Si el servicio Veeam está instalado en una instancia solo con red privada, porque la VSI Veeam está configurada sin acceso a la red pública, no puede comprobar si hay actualizaciones ni descargarlas mediante el propio software Veeam. En su lugar, debe descargar las actualizaciones desde el sitio web de Veeam, transferirlas a la VM de Veeam, y luego instalarlas.

## Actualización de licencias de Veeam
{: #managingveeam-update-license}

### Actualización de licencias de Veeam para las instancias desplegadas con red pública y privada
{: #managingveeam-update-license-public-private}

Si el servicio Veeam está instalado en una instancia con red pública y privada, puede actualizar la licencia de Veeam de forma automática o manual siguiendo las instrucciones de Veeam que encontrará en [Actualización de licencia]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html).

### Actualización de licencias de Veeam para las instancias desplegadas solo con red privada
{: #managingveeam-update-license-private}

Si el servicio Veeam está instalado en una instancia solo con red privada, debe anotar fecha de caducidad de la licencia y [ponerse en contacto con el servicio de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obtener ayuda con la actualización de la clave de licencia cuando haya que renovar.

## Sustitución de la VSI de Veeam de instancias anteriores a V1.8 con Veeam on IBM Cloud
{: #managingveeam-replace-vsi}

El servicio Veeam on {{site.data.keyword.cloud_notm}}, que puede hacer copia de seguridad de componentes de gestión y de cargas de trabajo, sustituye la VSI de Veeam anterior que venía integrada con VMware vCenter Server en los releases anteriores a V1.8 solo para los componentes de copia de seguridad y de gestión.

Debido a este cambio, el separador **Copia de seguridad y restauración** anterior de la página de detalles de la instancia se eliminó y los puntos de copia de seguridad para las instancias ya no están disponibles en la consola de {{site.data.keyword.vmwaresolutions_short}}, aunque la VSI de Veeam en instancias anteriores a V1.8 sigue funcionando.

Debe crear una incidencia de soporte de {{site.data.keyword.cloud_notm}} para obtener ayuda con una restauración. Además, la licencia de la VSI de Veeam en instancias anteriores a V1.8 caducó el 14 de octubre de 2017. Por lo tanto, debe sustituir la VSI de Veeam anterior por el nuevo servicio Veeam on {{site.data.keyword.cloud_notm}}.

Siga estos pasos:
1. En la consola de {{site.data.keyword.vmwaresolutions_short}}, pulse **Recursos** en el panel de navegación de la izquierda y luego pulse la instancia de destino.
2. En la página de detalles de instancia, pulse el separador **Actualización y parche**. Asegúrese de que ha actualizado la instancia a la versión V1.8.
3. Pulse el separador **Servicios**.
4. En el separador **Añadir servicios**, instale el servicio Veeam on {{site.data.keyword.cloud_notm}}.

Después de que se haya desplegado el nuevo servicio Veeam on {{site.data.keyword.cloud_notm}} y se haya realizado correctamente una copia de seguridad de los componentes de gestión, puede eliminar la VSI de Veeam existente de la cuenta mediante la creación de una incidencia de soporte de {{site.data.keyword.cloud_notm}}. El equipo de soporte de IBM identifica y suprime la VSI de Veeam existente y el almacenamiento.

## Enlaces relacionados
{: #managingveeam-related}

* [Visión general de Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Preguntas frecuentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Sitio web Veeam.com](https://www.veeam.com/)
* [Documentación técnica de Veeam](https://www.veeam.com/documentation-guides-datasheets.html)
