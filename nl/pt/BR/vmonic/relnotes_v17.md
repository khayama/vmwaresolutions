---

copyright:

  years:  2016, 2017

lastupdated: "2017-07-05"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Notas sobre a liberação para V1.7
{: #relnotes_v17}

Esta liberação inclui novos recursos, atualizações de componentes, aprimoramentos de usabilidade e correções de bug. Para obter uma lista de problemas corrigidos em diferentes liberações, problemas conhecidos com o produto e dicas para usar o {{site.data.keyword.vmwaresolutions_full}}, consulte o [{{site.data.keyword.vmwaresolutions_short}}dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Atualizações para instâncias do VMware Cloud Foundation
{: #relnotes_v17-vcf}

Essa atualização se aplica aos seguintes upgrades e melhorias:
* VMware SDDC Manager 2.3
* VMware NSX for vSphere 6.2.6
* VMware vCenter Server 6.0u3b
* VMware Security Patch 6.0 EP7c
* Melhorias de estabilidade para o componente IBM CloudDriver
* O modo EVC (com base no processador Intel “Haswell” 2690-V3) é ativado em implementações pré-existentes do VMware que estão em servidores V3 no momento do upgrade.

  O modo EVC não está ativado para implementações novas ou existentes em servidores V4.
  {:note}

* As implementações do VMware Cloud Foundation que foram implementadas antes de 22 de maio e, portanto, estão usando servidores V3 agora pedirão servidores V4 ao incluir um novo nó na instância. Esses servidores têm 256 GB de memória; se você precisar de 512 GB de memória, depois de incluir os servidores, abra um chamado de suporte para solicitar um upgrade do servidor para 512 GB de memória. Para obter mais informações sobre como entrar em contato com o Suporte IBM, consulte [Contatando o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).

### Requisitos do processo de atualização
{: #relnotes_v17-update-process}

Dependendo da complexidade de sua implementação de instância do Cloud Foundation e de você ter uma configuração de vários sites, o processo de atualização pode exigir uma sequência de etapas que devem ser concluídas conforme exibido na guia **Atualização e Correção** no console.

## Atualizações para instâncias do VMware vCenter Server
{: #relnotes_v17-vcs}

### Suporte de cluster
{: #relnotes_v17-cluster}

Começando com a liberação V1.7, é possível usar clusters para gerenciar servidores ESXi em instâncias do vCenter Server para um melhor gerenciamento de recursos e alta disponibilidade. Os servidores ESXi configurados quando você pediu uma instância são agrupados como **cluster1** por padrão. É possível visualizar os detalhes do cluster ou incluir até um total de cinco clusters em uma instância da guia **Infraestrutura** recém-introduzida na página de detalhes da instância. Quando você estiver expandindo ou contraindo a capacidade de uma instância, será possível selecionar em qual cluster incluir ou de qual cluster remover servidores ESXi. Para obter mais informações, consulte [Incluindo, visualizando e excluindo clusters para instâncias do vCenter Server](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters).

### Aprimoramentos para a implementação de recuperação de desastre do Zerto
{: #relnotes_v17-zerto}

A implementação da recuperação de desastre do Zerto é, agora, automatizada em vez de ser manipulada por meio de um chamado de suporte. Todos os componentes do Zerto, como uma sub-rede móvel privada, uma VSI (Virtual Service Instance) do Windows e os encargos de licença do Zerto são listados no custo estimado para que você possa revisar antes de fazer o seu pedido. Para obter mais informações, veja [Processo de implementação da recuperação de desastre do Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr).

### Recursos de upgrade de licença do NSX
{: #relnotes_v17-nsx}

É possível fazer upgrade de sua edição de licença do NSX da guia **Resumo** de sua instância do vCenter Server. O upgrade de licença substitui todas as licenças existentes do NSX SoftLayer em sua conta com a nova licença. Para obter mais informações, veja [Visualizando instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances).

## Aprimoramentos de usabilidade
{: #relnotes_v17-ui}

São feitas melhorias em toda a interface com o usuário:
* A guia **Propriedades** na página de detalhes da instância do Cloud Foundation é renomeada para **Resumo**. Agora, é possível visualizar detalhes da instância, as informações de acesso dos componentes relacionados à instância e o histórico de implementação da instância nessa guia.
* Uma nova guia **Infraestrutura** é introduzida na página de detalhes da instância do Cloud Foundation. É possível visualizar, incluir ou remover servidores ESXi nesta guia.
* A documentação para o {{site.data.keyword.vmwaresolutions_short}} tem um novo formato e agora está completamente integrada ao catálogo do Bluemix, juntamente com o conjunto de documentação do Bluemix. É possível acessar a documentação de uma das maneiras a seguir:
  * No {{site.data.keyword.vmwaresolutions_short}}, clique em **Docs** à esquerda do banner.
  * No catálogo de documentação do Bluemix, role para baixo para a seção **Cálculo e serviços** e clique em **{{site.data.keyword.vmwaresolutions_short}}**.
