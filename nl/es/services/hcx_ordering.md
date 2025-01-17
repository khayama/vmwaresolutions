---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Solicitud de VMware HCX on IBM Cloud
{: #hcx_ordering}

Puede solicitar el servicio de VMware HCX on {{site.data.keyword.cloud}} al pedir una instancia nueva de VMware vCenter Server con el paquete híbrido (Hybridity) incluida con el servicio o añadiendo el servicio a la instancia existente.

## Solicitud de VMware HCX on IBM Cloud para una nueva instancia
{: #hcx_ordering-new}

Para solicitar una nueva instancia de VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity) con VMware HCX on {{site.data.keyword.cloud_notm}}, seleccione **VMware HCX on IBM Cloud** en la sección **Servicios** al solicitar la instancia desde la consola de {{site.data.keyword.vmwaresolutions_short}}.


## Solicitud de VMware HCX on IBM Cloud para una instancia existente
{: #hcx_ordering-existing}

Para añadir el servicio de VMware HCX on {{site.data.keyword.cloud_notm}} a una instancia existente de VMware vCenter Server on {{site.data.keyword.cloud_notm}} con el paquete híbrido (Hybridity), visualice la instancia para la que desea añadir el servicio, pulse **Servicios** en el panel de navegación izquierdo y pulse **Añadir**.

## Configuración de VMware HCX on IBM Cloud
{: #hcx_ordering-config}

Para instalar HCX on {{site.data.keyword.cloud_notm}}, siga los valores siguientes:
1. Especifique el **Tipo de interconexión de HCX** seleccionando una de las opciones siguientes:
  * **Red pública:** HCX crea una conexión cifrada entre sitios de la red pública. El registro de licencia y la calibración se realizan a través de la red pública.
  * **Interconexión privada:** HCX crea una conexión cifrada entre sitios a través de la red privada. El registro de licencia y la calibración se realizan a través de la red pública.
  * **Red privada:** HCX crea una conexión cifrada entre sitios de la red privada. El registro de licencia y la medición se realizan a través de la red privada a través del proxy HTTP.
3. Si selecciona **Red privada**, complete los campos siguientes:
  * **Dirección proxy:** La dirección IPv4 del servidor proxy.
  * **Puerto de proxy:** El puerto del servidor proxy. El número de puerto suele ser 8080 o 3128.
  * **Nombre de usuario:** El nombre de usuario si es necesaria la autenticación de proxy.
  * **Contraseña:** La contraseña si es necesaria la autenticación de proxy.
  * **Volver a especificar contraseña:** Vuelva a especificar la contraseña para la validación de autenticación proxy.
2. Especifique el **Tipo de certificado de punto final público**. Si selecciona **Certificado de CA**, configure los valores siguientes:
  * **Contenido del certificado:** Especifique el contenido del certificado de CA.
  * **Clave privada:** Especifique la clave privada del certificado de CA.
  * (Opcional) **Contraseña:** Especifique la contraseña para la clave privada si está cifrada.
  * (Opcional) **Vuelva a escribir la contraseña:** Vuelva a escribir la contraseña para la clave privada.
  * (Opcional) **Nombre de host:** El nombre de host que se correlacionará con el nombre común (CN) del certificado de CA. HCX on {{site.data.keyword.cloud_notm}} requiere que el formato del certificado de CA esté aceptado por NSX Edge. Para obtener más información sobre los formatos de certificado NSX Edge, consulte [Importación de certificados SSL](https://docs.vmware.com/en/VMware-NSX-Data-Center-for-vSphere/6.3/com.vmware.nsx.admin.doc/GUID-19D3A4FD-DF17-43A3-9343-25EE28273BC6.html).
  <!--Need enhancement, it is still not clear what the key pair is used for, is it for connecting to NSX? This is not in architecture doc either. -->

## Proceso de despliegue de HCX on IBM Cloud
{: #hcx_ordering-deploy}

El despliegue de HCX on {{site.data.keyword.cloud_notm}} es automático. Tanto si solicita una instancia de vCenter Server con el paquete híbrido (Hybridity) con el servicio incluido como si despliega el servicio posteriormente en la instancia, los pasos siguientes se completan mediante el proceso de automatización de {{site.data.keyword.vmwaresolutions_short}}:
1. Se solicitan tres subredes para HCX desde la infraestructura de {{site.data.keyword.cloud_notm}}:
   * Una subred portátil privada para la gestión de HCX.
   * Una subred portátil privada para interconexiones HCX. Esta subred se utiliza cuando se selecciona la opción **Red privada** para el **tipo de interconexión HCX**.
   * Una subred portátil pública para la activación y mantenimiento con VMware. Si se selecciona la opción **Red pública** para el **tipo de interconexión HCX**, esta subred también se utiliza para interconexiones HCX.

   Las direcciones IP de las subredes solicitadas para HCX están pensadas para que las gestione el proceso automático de VMware en {{site.data.keyword.cloud_notm}}. Estas direcciones IP no se pueden asignar a recursos de VMware, como VM y NSX Edges, creados por el cliente. Si necesita direcciones IP adicionales para los artefactos de VMware, debe solicitar sus propias subredes de {{site.data.keyword.cloud_notm}}.
   {:important}
2. Si se ha seleccionado **Red privada** como **Tipo de interconexión de HCX**, se crea un grupo de puertos llamado **SDDC-DPortGroup-HCX-Private** en el conmutador virtual distribuido (DVS).
3. Se solicita a VMware una clave de activación de HCX.
4. Se crean tres agrupaciones de recursos y carpetas de VM para HCX, que son necesarias para las interconexiones de HCX, los componentes locales de HCX y los componentes remotos de HCX.
5. Se despliega y se configura un par de VMware NSX Edge Services Gateways (ESG) para el tráfico de gestión de HCX:
   * Se configuran interfaces de enlaces ascendentes públicos y privados utilizando las subredes solicitadas.
   * Se configuran los ESG como un par de dispositivos de extremo extra grandes con alta disponibilidad (HA) habilitada.
   * Se configuran reglas de cortafuegos y reglas de conversión de direcciones de red (NAT) para permitir el tráfico HTTPS de entrada y de salida procedente y destinado a HCX Manager.
   * Se configuran las agrupaciones de recursos y las reglas del equilibrador de carga. Estas reglas y agrupaciones de recursos se utilizan para reenviar el tráfico de entrada relacionado con HCX a los dispositivos virtuales adecuados de HCX Manager y vCenter Server (con el controlador de servicios de plataforma integrado).
   * Se aplica el certificado SSL para cifrar el tráfico HTTPS de entrada relacionado con HCX que llega a través de los ESG.

   El extremo de gestión HCX se dedica al tráfico de gestión HCX entre los componentes locales de HCX y los componentes en la nube de HCX. No modifique el extremo de gestión de HCX ni lo utilice para extensiones de red de HCX. En su lugar, crear otros extremos para extensiones de red. Además, el uso de un cortafuegos o la inhabilitación de las comunicaciones del extremo de gestión de HCX con componentes de gestión privados de IBM o con internet pública pueden afectar negativamente a las funciones de HCX.
   {:important}

6. Se despliega, se activa y se configura HCX Manager on {{site.data.keyword.cloud_notm}}:
   * Se registra HCX Manager con vCenter Server.
   * Se configuran los componentes HCX Manager, vCenter Server (con el controlador de servicios de plataforma integrado) y NSX Manager.
   * Se configura la flota HCX.
   * Se configuran contenedores de despliegue de HCX locales y remotos.
7. Se registra el nombre de host y la dirección IP de HCX Manager con el servidor DNS de VMware vCenter Server on {{site.data.keyword.cloud_notm}}.

## Enlaces relacionados
{: #hcx_ordering-related}

* [Visión general de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations)
* [Gestión de HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Solicitud, visualización y eliminación de servicios para instancias de vCenter Server con el paquete híbrido (Hybridity)](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [Glosario de términos de HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Cómo ponerse en contacto con el equipo de soporte de IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Visión general de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentación de VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
