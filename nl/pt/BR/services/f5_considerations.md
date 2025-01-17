---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# F5 no IBM Cloud Visão Geral
{: #f5_considerations}

O F5 no serviço {{site.data.keyword.cloud}} (F5 BIG-IP® Virtual Edition) fornece serviços inteligentes de gerenciamento de tráfego e balanceamento de carga L4-L7 em escala local e global, rede robusta e proteção de firewall de aplicativo da web e acesso a aplicativo seguro e federado.

É possível instalar mais de uma instância desse serviço, conforme necessário.

Esse serviço está disponível somente para instâncias que são implementadas na V1.9 ou mais recente. A versão do BIG-IP VE atual instalada é a v14.1.0.2.
{:note}

## Especificações técnicas para o F5 on IBM Cloud
{: #f5_considerations-specs}

Os componentes a seguir estão incluídos com o serviço F5 on {{site.data.keyword.cloud_notm}}:

### Máquinas virtuais
{: #f5_considerations-specs-vms}

* Duas máquinas virtuais (MVs) com todas as opções disponíveis.
* 2, 4 ou 8 vCPUs por máquina virtual, dependendo da opção de licenciamento.
* 4, 8 ou 16 GB de RAM por máquina virtual, dependendo da opção de licenciamento.

### Rede
{: #f5_considerations-specs-network}

* Virtual Extensible LAN (VXLAN) privada para sincronização de Alta disponibilidade (HA).
* Acesso ao Traffic Management Shell (TMSH) e ao Console de gerenciamento por meio da rede de gerenciamento privada.

### Licenças e taxas
{: #f5_considerations-specs-license}

As taxas de licença para cada MV são aplicadas a cada ciclo de faturamento, dependendo da opção de licenciamento (Bom, Melhor ou Excelente) e da largura da banda selecionada.

Não é possível mudar o nível de licenciamento após a instalação do serviço. Para mudar o nível de licenciamento, deve-se remover o serviço existente e reinstalá-lo usando uma opção de licenciamento diferente.
{:important}

## Considerações sobre instalação para o F5 on IBM Cloud
{: #f5_considerations-install}

Antes de instalar o F5 no serviço {{site.data.keyword.cloud_notm}}, revise as considerações a seguir.

Com base no modelo de licença e na largura de banda selecionados, duas MVs (máquinas virtuais) do BIG-IP VE são implementadas com a seguinte configuração:

Tabela 1. Implementações de CPU e de RAM para largura da banda diferente e seleções de modelo de licença

| Largura da banda máxima | Modelo de licença: Bom | Modelo de licença: Melhor | Modelo de licença: O Melhor |
|:------------------|:--------------------|:----------------------|:--------------------|
| 25 Mbps           | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 200 Mbps          | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 1 Gbps            | 2 vCPU, 4 GB de RAM    | 4 vCPU, 8 GB de RAM      | 8 vCPU, 16 GB de RAM   |
| 3 Gbps            | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |
| 5 Gbps            | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |
| 10 Gbps           | 8 vCPU, 16 GB de RAM   | 8 vCPU, 16 GB de RAM     | 8 vCPU, 16 GB de RAM   |

### Considerações Adicionais
{: #f5_considerations-additional}

* F5 BIG–IP limita o rendimento do dispositivo com base na largura máxima da banda escolhida. Como o desempenho de rede é afetado por muitos fatores, nem todas as configurações e topologias podem ser capazes de atingir a largura máxima da banda escolhida.
* O par de HA (Alta Disponibilidade) das MVs do BIG-IP VE será implementado apenas no cluster padrão.

  Além disso, 100% da CPU e da RAM para as duas MVs do BIG-IP VE também são reservados porque essas MVs estão no plano de dados das comunicações de rede e é fundamental que os recursos ainda estejam disponíveis para elas.

  Para calcular a reserva de CPU e de RAM para uma única MV do BIG-IP VE, use a fórmula a seguir:

  `Reserva de CPU = velocidade da CPU do servidor ESXi * número de vCPUs` (da Tabela 1)

  `Reserva de RAM = tamanho da RAM` (da Tabela 1)

### Considerações de Planejamento
{: #f5_considerations-planning}

Deve-se atender aos seguintes requisitos para evitar falhas com o F5 no {{site.data.keyword.cloud_notm}}:
* Pelo menos dois servidores ESXi ativos estão disponíveis para que as duas MVs do BIG-IP VE sejam implementadas com a regra de antiafinidade para manter as MVs em servidores separados.
* Os dois servidores ESXi ativos têm recursos suficientes disponíveis para que uma MV do BIG-IP VE possa ser hospedada em cada servidor ESXi com 100% de reserva de CPU e de RAM.
* O VMware vSphere HA tem recursos suficientes para hospedar duas MVs do BIG-IP com 100% de CPU e de RAM.

Devido a esses requisitos, deve-se planejar o espaço necessário para o F5 on {{site.data.keyword.cloud_notm}}. Se necessário, antes de pedir o F5 on {{site.data.keyword.cloud_notm}}, inclua 1-2 servidores ESXi em sua instância ou reduza a reserva de CPU do vSphere HA para failover, ou ambos.

## F5 no exemplo de pedido IBM Cloud
{: #f5_considerations-example}

Você pede uma instância **Pequena** do VMware vCenter Server com 2 servidores ESXI com a seguinte configuração: dezesseis núcleos a 2.10 GHz, cada um com 128 GB de RAM. Para o F5 no {{site.data.keyword.cloud_notm}}, selecione o modelo de licença **O Melhor** e um valor de 5 Gbps para **Largura máxima da banda**.

Nesse caso, uma única MV do BIG-IP requer, em cada servidor:
* 2,1 GHz * 8 vCPU = 16,8 GHz de CPU e
* 16 GB de RAM

No total, que é de 33,6 GHz de CPU e 32 GB de RAM para duas MVs do BIG-IP.

Cada servidor ESXi tem uma capacidade de 16 núcleos * 2,1 GHz = 33,6 GHz, então, nós encontramos os dois primeiro requisitos se ambos os servidores estiverem ativos e houver pelo menos 16,8 GHz de CPU e 16 GB de RAM disponível em cada servidor.

No entanto, por padrão, o vSphere HA reserva 50 por cento de CPU e de RAM para failover nas instâncias do vCenter Server que foram inicialmente implementadas com 2 servidores ESXi. Para esse exemplo, o seguinte está disponível:

`50% de 2 * 16 núcleos * 2,1 GHz = 33,6 GHz disponível`

Como haverá outras cargas de trabalho presentes nos servidores ESXi, por exemplo, VMware vCenter Server, VMware NSX Controller, VMware NSX Edge, usando esses recursos, não podemos satisfazer o terceiro requisito, porque precisamos de 33,6 GHz de CPU e 32 GB de RAM para as duas MVs do BIG-IP.

Nesse caso, o F5 na instalação do {{site.data.keyword.cloud_notm}} pode falhar, a menos que pelo menos um servidor ESXi seja incluído no ambiente e que as reservas de failover do vShpere HA sejam corretamente atualizadas para assegurar que haja recursos suficientes para as duas MVs do BIG-IP VE. Se recursos adicionais forem necessários para executar o F5 no serviço {{site.data.keyword.cloud_notm}}, será possível incluir mais servidores ESXi antes de instalar o F5 no {{site.data.keyword.cloud_notm}}.

## Considerações ao remover o F5 no IBM Cloud
{: #f5_considerations-remove}

Antes de remover o F5 no serviço {{site.data.keyword.cloud_notm}}, assegure-se de que a configuração existente do BIG-IP VE seja removida corretamente. Especificamente, o tráfego de rede deve ser roteado ao redor do BIG-IP VE em vez de através do BIG-IP VE. Caso contrário, o tráfego de dados existente do seu ambiente pode ser afetado.

## Links relacionados
{: #f5_considerations-related}

* [Solicitando F5 no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-f5_ordering)
* [Gerenciando o F5 no {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_f5)
* [Entrando em contato com o Suporte IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [Perguntas mais frequentes](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Website do F5](https://www.f5.com/){:new_window}
