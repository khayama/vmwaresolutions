---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Remarques relatives à la modification des artefacts vCenter Server
{: #vcenter_chg_impact}

Modifier des utilisateurs, des ressources ou des sous-réseaux réservés à {{site.data.keyword.vmwaresolutions_full}} peut avoir une incidence sur des opérations de gestion.

Ne modifiez pas les droits globaux du groupe **ic4v-vCenter** sur la page **Utilisateurs et groupes** du client Web VMware vSphere. Ces modifications incluent : la modification du nom d'utilisateur, la suppression de l'utilisateur ou la modification de son mot de passe.
Utilisez l'ID utilisateur hôte **root**. L'ID utilisateur hôte **ic4vroot** a été créé pour une utilisation IBM seulement.
{:important}

## ID d'automatisation
{: #vcenter_chg_impact-automation-id}
{: faq}

L'ID d'**automatisation** est un compte utilisateur qu'utilisent les opérations automatisées fournies par la console {{site.data.keyword.vmwaresolutions_short}}.

Les noms utilisateur et mots de passe des opérations automatisées dans la console ne doivent pas être modifiés, sinon les opérations effectuées à l'aide de la console qui dépendent de ces données d'identification risquent d'échouer.

## Comptes utilisateur de service
{: #vcenter_chg_impact-service-usr-account}
{: faq}

Chaque service crée un compte utilisateur interne dans vCenter Server. Ce compte est nécessaire pour que les opérations de gestion associées à un service puissent se connecter à vCenter Server afin d'effectuer les opérations sur le service.

Pour éviter les indisponibilités et les problèmes de connexion, si vous modifiez l'ID utilisateur, le mot de passe ou les paramètres d'expiration de mot de passe pour ce compte utilisateur, prenez soin de mettre également à jour les informations dans le service associé.
{:important}

L'ID utilisateur de ce compte est au format `<service_name>-<truncated service_uuid>@test.local` ou `<service_name>-<truncated service_uuid>@example-domain.local`. Par exemple, l'ID utilisateur dont se sert le service Veeam on {{site.data.keyword.cloud_notm}} pour se connecter à vCenter Server pour effectuer les sauvegardes planifiées est `Veeam-<Veeam_uuid>@test.local`.

Ensemble, le nom de service `<service_name>` et l'UUID du service `<service_uuid>` sont tronqués à 20 caractères.
{:note}

## Ressources VMware pour des instances vCenter Server (version 1.9 et ultérieures)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.9-and-later}
{: faq}

Pour les instances déployées en version 1.9 et ultérieures, si l'instance vCenter Server a le statut **Prêt à l'emploi**, vous pouvez modifier le centre de données virtuel VMware, le cluster, les commutateurs, les groupes de ports et le nom du magasin de données client à partir du client Web VMware vSphere.

Toutefois, vous ne devez pas modifier la valeur par défaut du nom du magasin de données de gestion, à savoir **vsanDatastore** pour les instances vSAN et **management-share** pour les instances NFS (Network File System). De plus, vous ne devez pas changer le nom des liaisons montantes du réseau qui sont créées durant la mise à disposition.

## Ressources VMware pour des instances vCenter Server (version 1.8 et antérieures)
{: #vcenter_chg_impact-vmware-resources-for-inst-v1.8-and-earlier}
{: faq}

Le tableau suivant répertorie les opérations susceptibles d'être affectées lorsque l'administrateur de la connexion unique modifie des ressources VMware vCenter Server en dehors de la console {{site.data.keyword.vmwaresolutions_short}}. Si une solution de récupération est disponible, elle est également fournie.

Ce tableau s'applique aux instances déployées en V1.8 et dans les éditions antérieures en plus des instances déployés en V1.8 et dans les éditions antérieures, puis mises à niveau vers V1.9 ou une édition ultérieure.

Tableau 1. Opérations affectées par des modifications de ressources VMware

| Modification  | Opérations affectées  | Gravité  | Méthode de récupération  |
|:------------- |:------------- |:--------------|:--------------|
| Modification du nom du centre de données virtuel VMware. | L'ajout d'un centre de données virtuel VMware risque d'échouer car le nouveau serveur ESXi ne peut pas contacter le centre de données virtuel modifié. | Important | Redonnez au centre de données virtuel VMware son nom d'origine. |
| Modification de noms de groupes de ports.    | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au groupe de ports son nom d'origine. |
| Modification du nom de cluster. | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au cluster son nom d'origine.
| Modification du nom du commutateur virtuel distribué (DVS, Distributed Virtual Switch) public ou privé. | L'ajout d'un serveur ESXi risque d'échouer. | Important | Redonnez au commutateur virtuel distribué public ou privé son nom d'origine.
| Modification du nom du magasin de données vSAN dans l'instance qui utilise vSAN. | L'ajout d'un serveur ESXi risque d'échouer.<br><br>La mise à niveau de l'instance risque d'échouer. | Important | Redonnez au magasin de données vSAN son nom d'origine, à savoir **vsanDatastore**.
| Modification du nom du magasin de données NFS de gestion dans l'instance qui utilise NFS. | L'ajout d'un serveur ESXi risque d'échouer.<br><br>La mise à niveau de l'instance risque d'échouer. | Important | Redonnez au magasin de données de gestion NFS son nom d'origine, à savoir **management-share** et remontez le magasin de données NFS en lecture seule sur le serveur ESXi.

Le tableau suivant répertorie les opérations susceptibles d'être affectées lorsque l'accès à SSH ou à l'interpréteur de commandes est désactivé pour différentes ressources.

Tableau 2. Opérations affectées pour l'accès à SSH et à l'interpréteur de commandes (local)

| Modification  | Opérations affectées  | Gravité  | Méthode de récupération  |
|:------------- |:------------- |:--------------|:--------------|
| Désactiver l'accès à SSH ou à l'interpréteur de commandes pour vCenter Server ou PSC. | L'appariement d'une instance principale et d'une instance secondaire peut échouer.    | Important    | Non applicable    |

Si vous choisissez de désactiver l'accès à SSH ou à l'interpréteur de commandes, vous devez le réactiver temporairement avant d'effectuer les opérations indiquées.

## Sous-réseaux de gestion pour des instances vCenter Server
{: #vcenter_chg_impact-mgmt-subnets}
{: faq}

Les informations suivantes concernent les sous-réseaux commandés par {{site.data.keyword.vmwaresolutions_short}} et indiquent les options de commande de sous-réseaux supplémentaires à votre usage personnel dont vous disposez.

**ATTENTION :** n'utilisez pas ces composants à d'autres fins ; vous risqueriez de compromettre grandement la stabilité de votre environnement.

Avec chaque commande de serveur bare metal {{site.data.keyword.cloud_notm}}, les plages d'adresses IP suivantes sont commandées par défaut :
*  Une plage publique principale de 32 adresses IP
*  Une plage privée principale de 64 adresses IP

De plus, les sous-réseaux de gestion suivants sont également réservés pour {{site.data.keyword.vmwaresolutions_short}} :
*  Deux sous-réseaux privés portables de 64 adresses IP sur le premier réseau local virtuel : un pour la gestion et l'autre pour le noeud final VTEPS
*  Deux sous-réseaux privés portables de 64 adresses IP sur le second réseau local virtuel : un pour VMotion et l'autre pour vSAN
*  Un sous-réseau public portable de 16 adresses IP sur le réseau local virtuel public

Si vous avez besoin de davantage de sous-réseaux, vous pouvez obtenir des adresses IP à utiliser de l'une des manières suivantes :
*  **Option 1 (recommandée)** : utilisez les superpositions de réseaux virtuels VMware NSX. Un exemple de modèle VXLAN est fourni lors de la commande. Ce modèle VXLAN peut être utilisé comme point de départ pour la génération de la mise en réseau définie par logiciel. Pour plus d'informations, voir [Configuration du réseau en vue d'utiliser la passerelle NSX Edge gérée par le client](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_esg_config).
*  **Option 2** : commandez vos propres sous-réseaux portables publics ou privés afin d'obtenir des adresses IP. Pour différentier les sous-réseaux que vous commandez des sous-réseaux de gestion, vous pouvez ajouter des notes aux sous-réseaux commandés.
