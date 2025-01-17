---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

---

# Cloud Foundation-Instanzen einer Version vor Version 2.5 auf IBM Cloud-Konten migrieren
{: #sd_addinstancetousraccount}

VMware Cloud Foundation-Instanzen, die in Version 2.5 und höheren Releases in Ihrem {{site.data.keyword.cloud}}-Konto bereitgestellt wurden, werden Ihrem Konto automatisch hinzugefügt und von {{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) verwaltet.

Bei Instanzen, die in Version 2.4 und älteren Releases bereitgestellt wurden, können Sie diese auf angegebene {{site.data.keyword.cloud_notm}}-Konten für das IAM-basierte Benutzermanagement migrieren.

## Vorbereitende Schritte
{: #sd_addinstancetousraccount-prereq}

Stellen Sie sicher, dass das {{site.data.keyword.cloud_notm}}-Konto, in das die Instanz migriert werden soll, nicht ein Nur-IaaS-Konto ist. Ein Nur-IaaS-Konto ist ein Konto der {{site.data.keyword.cloud_notm}}-Infrastruktur (SoftLayer), das keine Verbindung zu einem {{site.data.keyword.cloud_notm}}-Konto hat.

Weitere Informationen zum Verknüpfen Ihres Nur-IaaS-Kontos mit Ihrem PaaS-Konto finden Sie in [Folgen Sie diesen Schritten, um Ihr IaaS-Konto und Ihr PaaS-Konto zu verknüpfen](https://www.ibm.com/blogs/bluemix/2018/03/follow-steps-link-iaas-paas-accounts/).

## Vorgehensweise beim Migrieren von Instanzen
{: #sd_addinstancetousraccount-procedure}

1. Klicken Sie in der {{site.data.keyword.vmwaresolutions_short}}-Konsole im linken Navigationsfenster auf **Bereitgestellte Instanzen**.
2. Klicken Sie im Konsolenbanner auf das Symbol Ihres Benutzerkontos und klicken Sie anschließend auf das Feld **Konto**, um das Benutzerkonto auszuwählen, in das Sie die Instanz migrieren möchten.
3. Suchen Sie die Instanz der Version vor 2.5 in der Tabelle **Cloud Foundation-Instanzen**.
4. Klicken Sie in der Spalte **Aktionen** auf das Überlaufmenüsymbol und anschließend auf **Instanz auf Konto migrieren**.
5. Prüfen und bestätigen Sie im Fenster **Instanz auf Konto migrieren** das Konto, auf das die Instanz migriert werden soll, und klicken Sie auf **Migrieren**.

## Ergebnisse
{: #sd_addinstancetousraccount-results}

1. Sie empfangen eine Konsolbenachrichtigung, dass Ihre Anforderung zum Migrieren der Instanz auf das angegebene {{site.data.keyword.cloud_notm}}-Konto akzeptiert wurde.
2. Wenn die Instanzmigration abgeschlossen ist, wird die Instanz auf der Seite **Bereitgestellte Instanzen** unter dem Konto angezeigt, auf das sie migriert wurde. Die migrierte Instanz wird nicht mehr in dem ursprünglichen Konto angezeigt, aus dem sie migriert wurde.

## Zugehörige Links
{: #sd_addinstancetousraccount-related}

* [Benutzerzugriff mit IAM verwalten](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-managing-user-access-with-iam)
* [Benutzer für den Zugriff auf Services und Ressourcen einladen](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [Was ist IBM Cloud IAM?](/docs/iam?topic=iam-iamoverview)
