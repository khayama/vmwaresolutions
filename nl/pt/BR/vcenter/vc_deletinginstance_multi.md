---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Excluindo instâncias do vCenter Server em uma configuração de vários sites
{: #vc_deletinginstance_multi}

Esteja ciente das seguintes considerações especiais antes de planejar a exclusão de instâncias do vCenter Server que fazem parte de uma configuração multisite.

Quando você excluir uma instância do vCenter Server, os componentes a seguir serão liberados sequencialmente:
1. Todos os serviços implementados
2. Taxa de suporte e serviços
3. Licenças do produto VMware
4. Servidores ESXi
5. Subnets
6. VLANs

Devido a dependências de recursos, os componentes em sua instância não são liberados imediatamente quando você exclui a instância. Por exemplo, as sub-redes e VLANs não podem ser excluídas até que os servidores ESXi sejam totalmente recuperados pela infraestrutura do {{site.data.keyword.cloud}}, o que acontece no final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}. No final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}}, que geralmente é de 30 dias, as sub-redes e VLANs são excluídas e a exclusão da instância é concluída.

Você é faturado até o final do ciclo de faturamento da infraestrutura do {{site.data.keyword.cloud_notm}} para a instância excluída.
{:note}

## Procedimento para excluir instâncias do vCenter Server em uma configuração multisite
{: #vc_deletinginstance_multi-procedure}

1. Remova todos os serviços da instância secundária do vCenter Server.
2. Assegure-se de que nenhum objeto NSX seja expandido para a instância secundária que você deseja excluir.
3. Exclua o vCenter Server secundário do domínio SSO (Conexão única) primário. Para obter mais informações, veja [Cancelar o registro do vCenter Server da conexão única](https://kb.vmware.com/s/article/2106736){:new_window}.
4. Rebaixar a VSI (Virtual Service Instance) do controlador de domínio local. Para obter mais informações, veja [Rebaixando os controladores de domínio e os domínios](https://docs.microsoft.com/en-us/windows-server/identity/ad-ds/deploy/demoting-domain-controllers-and-domains--level-200-){:new_window}.
5. Exclua a instância secundária do vCenter Server do console do {{site.data.keyword.vmwaresolutions_short}}.
6. Repita as etapas 1 a 5 para todas as instâncias secundárias do vCenter Server em sua configuração multisite.
7. Depois de excluir todas as instâncias secundárias, também será possível excluir a instância primária do console do {{site.data.keyword.vmwaresolutions_short}}.

## Links relacionados
{: #vc_deletinginstance_multi-related}

* [Excluindo instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_deletinginstance)
* [Pedindo, visualizando e removendo serviços de instâncias do vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
