---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-22"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo, visualizando e removendo serviços para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservices}

É possível pedir serviços para a sua instância do VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle, como uma solução de recuperação de desastre. Quando você não precisar mais desses serviços, será possível removê-los de sua instância.

## Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservices-available-services}

Os serviços a seguir estão disponíveis para instâncias do vCenter Server with Hybridity Bundle, juntamente com as versões de serviço instaladas.

Tabela 1. Serviços disponíveis para instâncias do vCenter Server with Hybridity Bundle

| Nome do Serviço | Versão do serviço atual | Versão da instância |
|----------------------------------------------------------------------------------------|------------------|
| [Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_considerations) | 2.2 | V2.9 e mais recente |
| [F5 on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_considerations) | BIG-IP VE v14.1.0.2 | V1.9 e mais recentes |
| [FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)       | Série 300 | V1.8 e mais recentes |
| [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations) | 6.0.3 | V2.0 e mais recentes |
| [HyTrust CloudControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htcc_considerations)              | 5.5 | V2.3 e mais recentes |
| [HyTrust DataControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htdc_considerations)              | 4.3 | V2.3 e mais recentes |
| [HyTrust KeyControl on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-htkc_considerations)              | 4.3 | V2.5 e mais recente |
| [{{site.data.keyword.cloud_notm}} Private Hosted](/docs/services/vmwaresolutions/services?topic=vmware-solutions-icp_overview) | 3.1.2 | V2.7 e mais recente |
| [IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_considerations)  | 10.1.3 | V2.2 e mais recentes |
| [KMIP for VMware on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_considerations) | 2.0  | N/A |
| [Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations) | 9.5u4 | V1.8 e mais recentes |
| [VMware HCX on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx_considerations#hcx_considerations) | 3.5.1 | V2.3 e mais recentes |
| [Zerto on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr) | 6,5 de atualização 3 | V1.2 e mais recentes |

## Procedimento para incluir serviços em instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservices-adding-procedure}

Para aplicar um serviço à instância do vCenter Server with Hybridity Bundle, clique nos links da tabela para revisar as considerações do serviço. Em seguida, verifique os componentes implementados e siga as instruções nos tópicos de solicitação para fazer seu pedido.

### Resultados da instalação de serviço
{: #vc_hybrid_addingremovingservices-adding-results}

Quando a instalação do serviço for concluída com êxito, você será notificado por e-mail e o serviço será exibido na guia **Serviços** dos detalhes da instância com o status **Instalado**.

## Procedimento para visualizar serviços para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservices-viewing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja visualizar serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, clique em um serviço para revisar informações sobre ele, como o status de serviço e outros detalhes.
5. Dependendo do serviço visualizado, é possível acessar os consoles de serviço usando as credenciais fornecidas nos detalhes do serviço e é possível gerenciar o serviço daqui.

## Procedimento para remover serviços para instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_addingremovingservices-removing-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_short}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância da qual deseja remover serviços.
3. Clique em **Serviços** na área de janela de navegação esquerda.
4. Na página **Serviços**, localize a instância de serviço que você deseja remover e clique no ícone **Excluir**.
5. Na janela **Excluir serviços**, revise as considerações ou os avisos, se houver algum. Selecione **Eu entendo** e clique em **Excluir**.

### Resultados da remoção de serviço
{: #vc_hybrid_addingremovingservices-removing-results}

Depois que sua solicitação para remoção do serviço for aceita, o status do serviço mudará para **Removendo**.

Quando a remoção do serviço for concluída com êxito, você será notificado por e-mail e o serviço será removido da página **Serviços** da instância.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para os serviços removidos.
{:note}

## Links relacionados
{: #vc_hybrid_addingremovingservices-related}

* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
