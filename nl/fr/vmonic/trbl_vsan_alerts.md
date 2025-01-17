---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-04"

subcollection: vmware-solutions


---

# Avertissements et alertes concernant l'état de santé du SAN virtuel
{: #trbl_vsan_alerts}

## Problème
{: #trbl_vsan_alerts-problem}

Des alertes et des avertissements concernant des problèmes liés à l'état de santé du SAN virtuels peuvent s'afficher sur la page **Monitor** du client Web VMware vSphere.

## Résolution
{: #trbl_vsan_alerts-resolution}

Ces avertissements ne sont pas liés à des problèmes et ne sont pas engendrés par des problèmes de fonctionnement. Cependant, si vous voulez effacer les avertissements affichés sur le client Web vSphere,
procédez comme suit.

1. Accédez à http://partnerweb.vmware.com/service/vsan/all.json et sauvegardez le fichier JSON sur votre système local, sous le nom `all.json`.
2. Vérifiez que vous avez effectué les opérations indiquées dans [Délai d'attente de la console vCenter](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_timeout_vc_console).
3. Sur la page des détails de l'instance, cliquez sur **Console vCenter** et connectez-vous au client Web vSphere à l'aide des données d'identification affichées sur la console {{site.data.keyword.vmwaresolutions_full}}.
4. Sur le client Web vSphere, accédez à **Manage > Settings** et ouvrez la section **Virtual SAN > Health > HCL Database**. Cliquez sur **Update from file**, puis téléchargez le fichier `all.json` précédemment sauvegardé.
5. Pour effacer les avertissements, accédez au panneau **Alarms** en haut à droite du client Web vSphere. Cliquez avec le bouton droit de la souris sur chacune des alarmes et sélectionnez **Reset to green**.

Pour plus d'informations, voir [How to download offline vSAN HCL file for vSAN Health Check Plugin](https://www.virtuallyghetto.com/2015/05/how-to-download-offline-vsan-hcl-file-for-vsan-health-check-plugin.html){:new_window}.
