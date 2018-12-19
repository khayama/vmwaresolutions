---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-13"

---

# Componentes de serviços comuns

Os serviços comuns fornecem os serviços que são usados por outros serviços na plataforma de gerenciamento de nuvem. Os serviços comuns incluem serviços de identidade e acesso, serviços de nome de domínio e serviços NTP.

Figura 1. Serviços comuns do {{site.data.keyword.cloud}} Private (ICP)
![Serviços comuns do ICP](vcscar-common-services.svg)

## Serviços de identidade e de acesso

Como parte da automação do VMware vCenter Server on {{site.data.keyword.cloud_notm}}, um Microsoft Active Directory (AD) é
empregado para Gerenciamento de Identidade. Uma única instância de servidor virtual (VSI) do AD é implementada. O vCenter está configurado para usar a autenticação
do AD e é possível configurar o ICP também para a Autenticação
LDAP.

## Domain Name Services

A implementação usa as VSIs do AD
implementadas como servidores do Sistema de Nomes de Domínio (DNS) para a instância. Todos os componentes implementados são configurados para apontar para o AD como seu
DNS padrão. Os exemplos de componentes implementados incluem hosts vCenter, PSC, NSX e ESXi.

## Serviços do Network Time Protocol

A implementação do vCenter Server usa os servidores Network Time Protocol (NTP) da infraestrutura do {{site.data.keyword.cloud_notm}}.
Todos os componentes implementados são configurados para usar esses servidores NTP.
Ter todos os componentes que usam os mesmos servidores NTP
é crítico para que os certificados e a autenticação do AD funcionem
corretamente.

### Links relacionados

* [Visão geral do vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)