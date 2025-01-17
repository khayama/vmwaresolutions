---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Suppression d'instances VMware Federal

Pour libérer les composants commandés dans le cadre d'une instance VMware Federal, supprimez celle-ci.

Lorsque vous supprimez une instance VMware Federal, les composants suivants sont libérés, dans cet ordre :

1. Frais de support et de service
2. Licences de produit VMware
3. Serveurs ESXi
4. Sous-réseaux

En raison des dépendances de ressource, les composants de votre instance ne sont pas libérés immédiatement lorsque vous supprimez cette dernière. Par exemple, les sous-réseaux ne peuvent pas être supprimés tant que l'infrastructure {{site.data.keyword.cloud}} n'a pas récupéré tous les serveurs ESXi, opération qui s'effectue en fin de cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}. A la fin du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}, qui est généralement de 30 jours, les sous-réseaux sont supprimés et la suppression de l'instance est effective.

L'instance supprimée vous est facturée jusqu'à échéance du cycle de facturation de l'infrastructure {{site.data.keyword.cloud_notm}}.
{:note}

## Procédure de suppression d'instances dans la page Instances déployées

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, recherchez l'instance à supprimer.
3. Dans la colonne **Actions**, cliquez sur l'icône Supprimer.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Dans la colonne **Actions**, cliquez à nouveau sur l'icône Supprimer.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

## Procédure de suppression d'instances dans la page des détails de l'instance

1. A partir de la console {{site.data.keyword.vmwaresolutions_short}}, cliquez sur **Instances déployées** dans le panneau de navigation de gauche.
2. Dans le tableau **Instances vCenter Server**, cliquez sur l'instance à supprimer.
3. Cliquez sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   L'instance prend le statut **Suppression en cours**. Une fois l'instance supprimée, ses composants sont libérés et elle prend le statut **Supprimé**.
4. Si vous voulez supprimer l'enregistrement d'instance depuis la console {{site.data.keyword.vmwaresolutions_short}}, procédez comme suit :
   1. Cliquez à nouveau sur l'icône de menu déroulant dynamique en regard de **Console vCenter**, puis cliquez sur **Supprimer une instance**.
   2. Dans la fenêtre **Supprimer une instance**, cliquez sur **OK**.

### Liens connexes

* [Présentation de VMware Federal on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/vcenter/vc_fed_overview.html)
* [Commande d'instances VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_orderinginstance.html)
* [Sécurisation des instances VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_securinginstance.html)
* [Affichage des instances VMware Federal](/docs/services/vmwaresolutions/vcenter/vc_fed_viewinginstance.html)
* [Contacter le support IBM](/docs/services/vmwaresolutions/vmonic/trbl_support.html)
