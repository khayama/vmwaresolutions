---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-07"

subcollection: vmware-solutions


---

# Arquitetura multissite
{: #nsx-multi_site}

Um diferenciador principal entre o {{site.data.keyword.cloud}} e outras ofertas de nuvem é a capacidade de provisionar o recurso de computação dedicada em todo o mundo e conectar automaticamente a infraestrutura sob demanda com a rede dentro de sua conta privada do {{site.data.keyword.cloud_notm}}. Os recursos de rede definidos pelo software do VMware vCenter Server juntos com o {{site.data.keyword.cloud_notm}} fornecem uma infraestrutura global granular que pode ser construída em dias. As seções a seguir descrevem um exemplo de arquitetura multissite do que pode ser obtido com o recurso pronto para utilização do vCenter Server.

## Ambiente do cross-vCenter NSX
{: #nsx-multi_site-cross-env}

O recurso cross-vCenter NSX permite a vinculação em um relacionamento primário e secundário de até nove gerenciadores NSX: um primário e oito secundários. Embora não seja necessário ter servidores vCenter em um relacionamento do Enhanced Linked Mode (ELM) para que o cross-vCenter NSX funcione, isso fornece os benefícios a seguir:

* Criação simplificada de relacionamento primário e secundário usando credenciais de Conexão Única (SSO)
* Configuração de automação do vCenter Server para resolução do nome DNS para todos os sites que estão vinculados juntos
* Área de janela única de gerenciamento de vidro em todos os sites para as funções normais do vCenter e do NSX

## Exemplo de multissite
{: #nsx-multi_site-example}

O exemplo a seguir inclui uma zona de transporte universal do NSX nas topologias básicas de gerenciamento e de carga de trabalho que são discutidas nas seções anteriores e também inclui as características a seguir:

* A zona de transporte universal abrange dois {{site.data.keyword.CloudDataCents_notm}} ou PODs dentro de um {{site.data.keyword.CloudDataCent_notm}}.
* Após a zona de transporte ser incluída, múltiplas VXLANs são incluídas com um Universal Distributed Router que abrange as novas VXLANs.
* Deve-se configurar uplinks para os ESGs de carga de trabalho em ambos os sites. Essa configuração permite que máquinas virtuais (MVs) no site local atravessem seu ESG local.
* Para o tráfego de entrada, é necessário um balanceador de carga global. Veja as ofertas de balanceamento de carga global do {{site.data.keyword.cloud_notm}} para atender a esse requisito.
* Este exemplo requer edição do VMware NSX Enterprise.

![Topologia multisite](../../images/multisite_topology.svg "Topologia multisite")

## Links relacionados
{: #nsx-multi_site-related}

* [ Serviços de rede no  {{site.data.keyword.cloud_notm}} ](/docs/services/vmwaresolutions/archiref/nsx?topic=vmware-solutions-nsx-networking_services)
