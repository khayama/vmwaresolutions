---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Configuration multisite pour des instances Cloud Foundation
{: #sd_multisite}

{{site.data.keyword.vmwaresolutions_full}} permet de déployer des instances dans différents emplacements et de les rendre actives et opérationnelles très rapidement.

## Remarques
{: #sd_multisite-notes}

* Vous ne pouvez pas lier des instances VMware Cloud Foundation à des instances VMware vCenter Server dans une configuration multisite.
* Vous ne pouvez pas lier des instances déployées en version 2.0 à des instances d'éditions antérieures (même si ces dernières ont été mises à niveau vers la version 2.0).

## Composants d'un déploiement multisite
{: #sd_multisite-deployment-components}

Un déploiement multisite est constitué des composants suivants.

* **Instance principale** : l'instance principale VMware Cloud Foundation présente la configuration suivante :
  *  Domaine racine Microsoft Active Directory (AD) et système de noms de domaine (DNS, Domain Name System)
  *  Sous-domaine Cloud Foundation
  *  Domaine de connexion unique
  *  Nom de site de connexion unique
* **Instance ou instances secondaires** : une ou plusieurs instances Cloud Foundation liées à l'instance principale, qui présentent la configuration suivante :
   *  Nom de site de connexion unique
   *  Sous-domaine DNS lié au domaine racine sur l'instance principale
   *  Réplication DNS et AD configurée entre les machines virtuelles AD de l'instance principale et des instances secondaires
   *  Contrôleur PSC (Platform Services Controller) déployé et configuré de manière à répliquer le contrôleur PSC de l'instance principale
   *  VMware vCenter sur les instances secondaires configuré en mode lien étendu (Enhanced Linked) sur le serveur vCenter de l'instance principale

## Déploiement multisite Cloud Foundation
{: #sd_multisite-deployment}

Le modèle de configuration multisite utilise un concentrateur et une topologie en étoile (hub and spoke) avec un site principal et un maximum de sept sites secondaires. Une seule couche de sites est prise en charge, c'est-à-dire que vous ne pouvez pas configurer de sites supplémentaires qui sont liés à d'autres sites secondaires. Une configuration multisite accepte jusqu'à 128 serveurs ESXi répartis dans toutes les instances.

Si votre configuration nécessite un déploiement multisite de plus de 128 serveurs ESXi, contactez le support IBM pour obtenir de l'aide. Pour plus d'informations, voir [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support).
{:note}

Le graphique suivant décrit l'architecture globale d'un déploiement Cloud Foundation multisite.

Figure 1. Déploiement Cloud Foundation multisite

![Déploiement multisite de Cloud Foundation](../vcenter/multisite-hub-spoke.svg "Déploiement multisite de Cloud Foundation")

Le modèle contient les couches suivantes :

* **Instance principale** : dans une configuration multisite, la première instance a été définie en tant qu'instance principale au cours du processus de commande de l'instance.
* **Instances secondaires** : dans une configuration multisite, les instances liées à l'instance principale ont été définies en tant qu'instances secondaires au cours du processus de commande.

Vous pouvez avoir jusqu'à 8 instances (1 principale et 7 secondaires) au maximum déployées dans une configuration multisite.

La suppression d'instances Cloud Foundation qui font partie d'une configuration multisite requiert une planification spéciale. Pour plus d'informations, voir [Suppression d'instances Cloud Foundation dans une configuration multisite](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi).
{:note}

## Liens connexes
{: #sd_multisite-related}

* [Attribuer un rôle principal à NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [Configurer les NSX Manager secondaires](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [Active Directory Trusts supported with VMware vCenter Single Sign-On](https://kb.vmware.com/kb/2064250){:new_window}
* [Securely connect your private VMware workloads in the {{site.data.keyword.cloud_notm}}](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}
