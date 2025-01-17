---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-30"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Aplicando atualizações de componente de gerenciamento da IBM às instâncias do vCenter Server with Hybridity Bundle
{: #vc_hybrid_applyingupdates}

O procedimento nesta seção se aplica à atualização de componentes de gerenciamento da IBM para instâncias que são implementadas na V2.3 e V2.4.

Para instâncias implementadas em (ou submetidas a upgrade para) V2.5 ou mais recente, as atualizações e correções para os componentes de gerenciamento da IBM são aplicadas automaticamente, conforme necessário.

Além disso, observe o comportamento a seguir quando concluir determinadas operações em sua instância:
* Quando você pede novos serviços, a instância é atualizada para a versão mais recente.
* Quando você inclui novos clusters, esses clusters são provisionados com os componentes mais recentes do VMware, mas os clusters existentes não são.
* Ao incluir novos servidores ESXi, esses servidores ESXi são provisionados com os componentes mais recentes do VMware, mas os servidores ESXi existentes não são.

O {{site.data.keyword.vmwaresolutions_short}} não oferece suporte para aplicar atualizações e correções aos componentes do VMware. Deve-se monitorar e aplicar essas atualizações sozinho.
{:important}

## Antes de aplicar as atualizações de componente de gerenciamento da IBM
{: #vc_hybrid_applyingupdates-prereq}

Expanda a entrada de atualização clicando na seta para baixo e verifique as informações a seguir:
* A versão da atualização. Deve-se aplicar as atualizações em sequência cronológica que é da mais antiga para a mais recente. Assegure-se de que tenha aplicado todas as atualizações anteriores antes de aplicar a mais recente. Por exemplo, deve-se aplicar a atualização V2.3 antes de tentar aplicar a atualização V2.4.
* Se o tempo de inatividade é necessário.
* O tempo estimado total para concluir a atualização.
* O impacto da atualização no ambiente virtual do VMware.
* Os detalhes da atualização.

A tabela a seguir mostra como os diferentes níveis de impacto afetam o sistema.

Tabela 1. Atualize os níveis e o impacto

| Nível de atualização  | Impacto        |  
|:------------- |:------------- |
| Baixo    | Esta atualização não afeta nenhum sistema. Não é necessário aplicá-lo durante o tempo de inatividade planejado. |  
| Médio | Esta atualização pode afetar alguns sistemas. Recomenda-se aplicar durante o tempo de inatividade planejado. |  
| Grave  | Esta atualização afeta alguns ou todos os sistemas. Deve-se aplicá-lo durante o tempo de inatividade planejado. |  

## Procedimento para aplicar as atualizações de componente de gerenciamento da IBM (instâncias V2.3 e V2.4)
{: #vc_hybrid_applyingupdates-procedure}

1. No console do {{site.data.keyword.vmwaresolutions_full}}, clique em **Recursos** na área de janela de navegação esquerda.
2. Na tabela **Instâncias do vCenter Server**, clique na instância a ser atualizada.
3. Na página **Resumo**, verifique se todos os detalhes da instância são exibidos corretamente. Em seguida, clique em **Infraestrutura** na área de janela de navegação esquerda para verificar os detalhes na página **Infraestrutura**.

   Se os detalhes não forem exibidos, isso poderá indicar um problema de conectividade com a Virtual Server Instance (VSI) do IBM CloudDriver, como resultado de uma regra de firewall ou outro problema de rede. Resolva o problema antes de continuar com a próxima etapa, caso contrário, a atualização poderá falhar.

4. Clique em **Atualizar e corrigir** na área de janela de navegação esquerda e clique na seta para baixo para expandir a atualização de gerenciamento da IBM que você deseja aplicar e, em seguida, conclua uma das etapas a seguir:
   * Para iniciar a atualização imediatamente, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Atualizar agora**.
   * Para planejar uma atualização futura, clique no ícone de menu overflow na coluna **Ações** da entrada de atualização e, em seguida, clique em **Planejar atualização**. Selecione a data, o horário e o fuso horário quando desejar que a atualização seja iniciada. Clique em **OK**.

5. Se você estiver aplicando atualizações a instâncias na configuração de implementação multissite, uma seção intitulada **Etapas necessárias para atualizar** será exibida. Esta seção lista as operações de atualização necessárias para todas as instâncias na implementação de vários sites. Deve-se concluir as etapas em sequência clicando em **Aplicar atualização** para cada etapa. Deve-se aguardar a conclusão da etapa anterior antes de iniciar a próxima etapa.

## Resultados após a aplicação de atualizações de componente de gerenciamento da IBM
{: #vc_hybrid_applyingupdates-results}

1. Depois que uma atualização for aplicada, aparecerá um registro na lista de status de atualização de software, no qual é possível visualizar o progresso detalhado e o status da atualização. Quando a atualização for concluída com êxito, um registro aparecerá na lista de atualizações de softwares instalados.

  Para recuperar o status mais recente para uma tarefa de atualização, clique no ícone de atualização no canto superior direito da página.
  {:tip}

2. Para obter detalhes sobre os status de atualização, veja a lista a seguir:
<dl class="dl">
<dt class="dt dlterm">Disponível</dt>
<dd class="dd">A atualização está disponível para ser aplicada. Não é possível selecionar uma atualização disponível até que todas as suas atualizações anteriores sejam aplicadas.
</dd>
<dt class="dt dlterm">Em andamento</dt>
<dd class="dd">A tarefa de atualização foi iniciada, mas não foi concluída ainda. Não será possível aplicar nenhuma outra atualização até que a tarefa de atualização atual esteja concluída.</dd>
<dt class="dt dlterm">Instalado</dt>
<dd class="dd">A tarefa de atualização está concluída. O componente correspondente da plataforma VMware foi atualizado.</dd>
<dt class="dt dlterm">Com falha</dt>
<dd class="dd">A tarefa de atualização falha. O console relata um erro para a falha de atualização. Revise o erro e corrija o problema relatado antes de reaplicar a atualização.</dd>
<dt class="dt dlterm">Planejado</dt>
<dd class="dd">A tarefa de atualização está planejada para um momento posterior. A tarefa de atualização é iniciada automaticamente no momento planejado.</dd>
<dt class="dt dlterm">Desconhecido</dt>
<dd class="dd">O status da tarefa de atualização não pode ser obtido. Entre em contato com o Suporte IBM para obter assistência.</dd>
</dl>

3. Se o processo de atualização falhar em uma etapa específica, [entre em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) para obter assistência. Você será avisado sobre como resolver o problema e orientado a tentar o upgrade novamente a partir da etapa que falhou.

## Links relacionados
{: #vc_hybrid_applyingupdates-related}

* [VCenter Server with Hybridity Bundle Visão Geral](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_overview)
* [Fazendo upgrade de licenças para instâncias do vCenter Server with Hybridity Bundle](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_upgrade-lic)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas Mais Frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
