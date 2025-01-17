---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ajustando a escala dos clusters do vSphere existentes
{: #vs_scalingexistingclusters}

É possível escalar um cluster do VMware vSphere que você solicitou ou salvou no console do {{site.data.keyword.vmwaresolutions_full}}. Para fazer isso, inclua servidores ESXi ou solicite um par de HA do FortiGate 300 Series Security Appliance para o cluster.

## Requisitos
{: #vs_scalingexistingclusters-req}

Assegure-se de que tenha concluído as tarefas a seguir:
*  Você configurou as credenciais de infraestrutura do {{site.data.keyword.cloud_notm}} na página **Configurações**. Para obter mais informações, veja [Contas e configurações do usuário](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount#managing-user-accounts-and-settings).
*  Você revisou os requisitos e as considerações em [Requisitos e planejamento para clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_planning).
*  Você recebeu um e-mail com a confirmação de que o cluster que você deseja escalar está pronto para uso.

## Procedimento para escalar clusters existentes
{: #vs_scalingexistingclusters-procedure}

1. No catálogo do {{site.data.keyword.cloud_notm}}, clique em **VMware** na área de janela de navegação à esquerda e, em seguida, clique em **VMware vSphere** na seção **Datacenters virtuais**.
2. Na página **VMware vSphere on IBM Cloud**, clique em **Criar**.  
3. Clique na guia **Escala existente** e selecione o cluster que você deseja escalar na lista **Configurações do cluster**.
4. Revise as configurações do cluster que são concluídas automaticamente.
5. Na seção **{{site.data.keyword.baremetal_short}}**, especifique o número de {{site.data.keyword.baremetal_short}} que você deseja incluir no cluster.
6. Se o cluster não incluir o Par de HA do FortiGate 300 Series Security Appliance em sua VLAN pública, será possível pedir o dispositivo. Para fazer isso, marque a caixa de seleção **Incluir com compra** sob **Par de HA do FortiGate Physical Appliance 300 Series**.
7. Na área de janela **Resumo do pedido**, verifique a configuração da instância e o custo estimado.
   * Para salvar a configuração como um modelo sem fazer um pedido, clique em **Salvar configuração**.
   * Para fazer o pedido, assegure-se de que a conta a ser cobrada está correta, revise e aceite os termos e, em seguida, clique em **Provisão**.

### Resultados
{: #vs_scalingexistingclusters-results}

O ajuste de escala do cluster é iniciado automaticamente. Você recebe uma confirmação por e-mail de que a ordem está sendo processada. Quando o cluster estiver pronto para usar, você será notificado por e-mail.

Se o cluster que você está escalando não estiver pronto para uso, uma mensagem de erro poderá ser recebida.

Os clusters do vSphere, ao contrário das instâncias do vCenter Server, não são exibidos na página **Recursos**.
{:note}

## Links relacionados
{: #vs_scalingexistingclusters-related}

* [Pedindo novos clusters do vSphere](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderinginstances)
* [Pedindo clusters do vSphere com base nas configurações existentes](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingbasedonexistingconfig)
* [Ajustando a escala de clusters criados fora do console](/docs/services/vmwaresolutions/vsphere?topic=vmware-solutions-vs_orderingforclustersoutside)
