---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}

# Solicitud de KMIP for VMware on IBM Cloud - en desuso
{: #kmip_ordering}

La versión actual de KMIP for VMware on IBM Cloud ha quedado en desuso. Para obtener más información, [póngase en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html).
{:deprecated}

Puede solicitar el servicio de KMIP for VMware on {{site.data.keyword.cloud}} cuando pida una instancia nueva incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de KMIP for VMware on IBM Cloud para una instancia nueva
{: #kmip_ordering-new}

Puede solicitar una instancia nueva con KMIP for VMware on {{site.data.keyword.cloud_notm}} utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, al solicitar una instancia nueva, seleccione **KMIP for VMware on IBM Cloud** en la sección **Servicios**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **KMIP for VMware on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia nueva**.

## Solicitud de KMIP for VMware on IBM Cloud para una instancia existente
{: #kmip_ordering-existing}

Puede añadir el servicio de KMIP for VMware on {{site.data.keyword.cloud_notm}} en una instancia existente utilizando uno de los métodos siguientes:
* Desde la consola de {{site.data.keyword.vmwaresolutions_short}}, visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.
* Desde el catálogo de {{site.data.keyword.cloud_notm}}, seleccione **KMIP for VMware on IBM Cloud**, especifique los valores de servicio y seleccione **Añadir a instancia existente**.

## Configuración de servicio de KMIP for VMware on IBM Cloud
{: #kmip_ordering-config}

Al solicitar este servicio, proporcione los valores siguientes:

### Región de servicio
{: #kmip_ordering-service-region}

Seleccione la región de {{site.data.keyword.cloud_notm}} en la que se va a alojar su instancia del servicio KMIP for VMware {{site.data.keyword.cloud_notm}}.

{{site.data.keyword.cloud_notm}} mantiene un punto final altamente disponible del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}} en cada región en la que está disponible el servicio.

### Certificado SSL de cliente
{: #kmip_ordering-ssl}

Para vCenter Server, debe configurar un clúster de Key Management Server (KMS). El punto final en su región seleccionada se conecta de forma segura al KMS mediante el certificado SSL cliente. Consulte la tabla siguiente para el punto final de cada región. Estos puntos finales utilizan certificados autofirmados que mantiene el equipo de {{site.data.keyword.vmwaresolutions_short}}. El certificado de huella de los certificados es `a9 d0 ff 15 df 85 10 6b 61 88 fe 2e 8b d3 1a af 48 c8 a0 7a`.

Tabla 1. Regiones de puntos finales del servicio KMIP for VMware on {{site.data.keyword.cloud_notm}}

| Región         | Punto final               |
|:---------------|:-----------------------|
| Alemania        |  `161.156.68.107:5696` |
| Sídney         |  `130.198.73.134:5696` |
| Reino Unido |  `158.175.93.122:5696` |
| EE.UU. sur       |  `169.60.185.42:5696`  |

Este valor es opcional en el momento de la configuración inicial. Puede dejar este campo en blanco porque el certificado de cliente del KMS in vCenter Server se conoce después de que se despliegue la instancia. Pero debe especificar el certificado después de que se despliegue la instancia para que se pueda realizar correctamente la conexión de vCenter Server con KMS.

### Clave de API para ID de servicio
{: #kmip_ordering-api-key}

Especifique la clave de API para el ID de servicio de {{site.data.keyword.cloud_notm}} que se utiliza para acceder a la instancia de IBM Key Protect Service.

### Instancia de Key Protect
{: #kmip_ordering-key-protect}

Pulse **Recuperar** para obtener la lista de instancias disponibles de IBM Key Protect Service y seleccione la que se utilizará para la gestión de claves.

### Clave raíz de cliente
{: #kmip_ordering-root-key}

Pulse **Recuperar** para obtener la clave raíz del cliente que se almacena en la instancia de IBM Key Protect seleccionada.

## Enlaces relacionados
{: #kmip_ordering-related}

* [Visión general de KMIP for VMware on {{site.data.keyword.cloud_notm}}](kmip_considerations.html)
* [Solicitud, visualización y eliminación de servicios para instancias de Cloud Foundation](../sddc/sd_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server](../vcenter/vc_addingremovingservices.html)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](../vcenter/vc_hybrid_addingremovingservices.html)
* [Sucesos de {{site.data.keyword.cloudaccesstrailshort}}](../vmonic/at-events.html)
* [IBM Key Protect para {{site.data.keyword.cloud_notm}}](../../keymgmt/index.html)
* [Seguridad de vSphere](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.security.doc/GUID-52188148-C579-4F6A-8335-CFBCE0DD2167.html)
* [Preguntas frecuentes](../vmonic/faq.html)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](../vmonic/trbl_support.html)
