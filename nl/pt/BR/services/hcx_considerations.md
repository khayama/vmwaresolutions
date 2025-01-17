---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-23"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware HCX on IBM Cloud Visão Geral
{: #hcx_considerations}

O serviço HCX on {{site.data.keyword.cloud}} amplia perfeitamente as redes de data centers no local para o {{site.data.keyword.cloud_notm}}, o que permite que você migre máquinas virtuais (MVs) para e do {{site.data.keyword.cloud_notm}} sem nenhuma conversão ou mudança.

Esse serviço está disponível somente para instâncias do VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle que são implementadas na V2.3 e mais recente. A versão atual do HCX on {{site.data.keyword.cloud_notm}} que está instalada é 3.5.1.
{:note}

É possível fazer upgrade de sua instância do vCenter Server existente para uma instância do vCenter Server with Hybridity Bundle. Para obter mais informações sobre como fazer upgrade de sua instância e implementar o serviço HCX on {{site.data.keyword.cloud_notm}}, consulte [Procedimento para fazer upgrade para o Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_upgrade-lic#vc_upgrade-lic-procedure-upgrade-to-hybridity).

Uma instância do vCenter Server com HCX no {{site.data.keyword.cloud_notm}} é limitada a três conexões simultâneas por meio de sites no local.
{:note}

## Especificações técnicas para HCX on IBM Cloud
{: #hcx_considerations-specs}

Os componentes a seguir são ordenados e incluídos no serviço HCX on {{site.data.keyword.cloud_notm}}.

As instâncias do HCX local incluem apenas licenciamento e ativação.
{:note}

### Um par ativo/passivo de VMware NSX Edge Services Gateways para gerenciamento do HCX
{: #hcx_considerations-nsx}

* CPU: 6 vCPU
* RAM: 8 GB
* Disco: 3 GB VMDK

### Dispositivo de gerenciamento HCX - máquina virtual
{: #hcx_considerations-vm}

* CPU: 4 vCPU
* RAM: 12 GB
* Disco: VMDK de 60 GB

Os dispositivos HCX adicionais são implementados durante a configuração, conforme necessário, para conectividade L2, otimização de WAN e conexões de gateway.

### Rede
{: #hcx_considerations-networking}

* Uma sub-rede móvel pública com 16 endereços IP
* Duas sub-redes portáteis privadas com 64 endereços IP
* Oito endereços IP da sub-rede vMotion móvel privada

## Considerações ao instalar o HCX on IBM Cloud
{: #hcx_considerations-install}

Revise as considerações a seguir antes de tentar instalar o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos no número de servidores ESXi
{: #hcx_considerations-esxi-servers}

O serviço HCX no {{site.data.keyword.cloud_notm}} não pode ser instalado em uma instância para a qual o cluster padrão tem mais de 51 servidores ESXi. Como o HCX no {{site.data.keyword.cloud_notm}} requer oito endereços IP na sub-rede do vMotion no cluster padrão, se o número de servidores ESXi exceder 51, nenhum endereço IP na sub-rede do vMotion estará disponível para o HCX no {{site.data.keyword.cloud_notm}}.

### Requisitos em regras de firewall
{: #hcx_considerations-firewall}

Antes de instalar o serviço HCX on {{site.data.keyword.cloud_notm}}, deve-se incluir uma regra de firewall em quaisquer firewalls existentes para permitir todo o tráfego HTTPS de saída para que o dispositivo virtual HCX Manager (HCX Manager) possa se registrar. Após a conclusão da instalação do HCX Manager, você poderá remover a regra de firewall. Além disso, deve-se configurar regras de firewall para permitir que o HCX funcione corretamente. Para obter mais informações, consulte [Requisitos de acesso à porta do VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-port-req#hcx-archi-port-req).

## Considerações ao remover o HCX on IBM Cloud
{: #hcx_considerations-delete}

Revise as considerações a seguir antes de remover o serviço HCX no {{site.data.keyword.cloud_notm}}:
* Assegure-se de que as interconexões e as redes estendidas entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidas. Para remover as interconexões e as redes estendidas, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* Assegure-se de que os pares de site entre o site de origem no local e os sites de destino do {{site.data.keyword.cloud_notm}} sejam removidos. Para remover os pares de site, use a interface com o usuário HCX no VMware vSphere Web Client no local.
* A remoção do HCX no {{site.data.keyword.cloud_notm}} é automatizada. Os procedimentos a seguir são concluídos para a remoção bem-sucedida desse serviço:
   * A licença do HCX pedida para o HCX Manager do lado da nuvem é desativada.
   * O gerenciador de HCX é excluído.
   * Os endereços IP do vMotion que foram reservados para o HCX são liberados.
   * Se vazios, os conjuntos de recursos relacionados ao HCX são removidos.
   * Se vazias, as pastas relacionadas ao HCX são removidas.
   * Os dispositivos de borda de gerenciamento do HCX são excluídos.

## Links relacionados
{: #hcx_considerations-related}

* [Solicitando HCX no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_ordering)
* [Gerenciando o HCX no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managinghcx)
* [Glossário de termos do HCX](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_glossary)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Visão geral do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx)
* [Documentação do VMware Hybrid Cloud Extension](https://cloud.vmware.com/vmware-hcx/resources)
