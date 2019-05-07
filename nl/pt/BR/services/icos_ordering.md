---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-20"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Pedindo e configurando o IBM Cloud Object Storage com o Veeam
{: #icos_ordering}

Com a liberação do Veeam Availability Suite 9.5 Atualização 4, o Veeam é compatível com o IBM Cloud Object Storage (ICOS). O pedido do IBM Cloud Object Storage não é automatizado ao pedir o Veeam on IBM Cloud, mas pode ser incluído após a implementação.

Para pedir o IBM Cloud Object Storage, conclua as tarefas a seguir no pedido especificado.

## Criando uma instância do Object Storage
{: #icos_ordering-obj}

Para criar uma instância do Object Storage, consulte [Criar uma nova instância de serviço](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-order-storage#creating-a-new-service-instance). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Criando um depósito
{: #icos_ordering-bucket}

Para criar um depósito, consulte a [Etapa 1: Criar alguns depósitos para armazenar os seus dados](https://cloud.ibm.com/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-getting-started-console-#create-buckets). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Criando credenciais de serviço
{: #icos_ordering-service-cred}

Para criar credenciais de serviço, incluindo credenciais do HMAC, consulte [Credenciais de serviço](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Incluindo um repositório de dimensionamento
{: #icos_ordering-scale-repo}

Para incluir um repositório de dimensionamento no Veeam, consulte [Incluindo repositórios de dimensionamento](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}. Siga as etapas e retorne para esta seção para continuar com as tarefas a seguir.

## Mantendo e gerenciando a sua camada de nuvem
{: #icos_ordering-manage-cloud}

Para obter informações sobre a manutenção e o gerenciamento de sua camada de nuvem, consulte [Gerenciando dados da camada de capacidade](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}.