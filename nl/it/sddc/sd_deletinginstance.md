---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Eliminazione di istanze Cloud Foundation
{: #sd_deletinginstance}

Per rilasciare i componenti che hai ordinato in un'istanza VMware Cloud Foundation, elimina l'istanza.

Quando elimini un'istanza Cloud Foundation, i seguenti componenti vengono rilasciati in modo sequenziale:
1. Tutti i servizi distribuiti
2. Tariffa per supporto e servizi
3. Licenze del prodotto VMware
4. Server ESXi
5. Sottoreti
6. VLAN

A causa delle dipendenze delle risorse, i componenti della tua istanza non vengono rilasciati immediatamente quando elimini l'istanza. Ad esempio, le sottoreti e le VLAN non possono essere eliminate finché i server ESXi non vengono completamente recuperati dall'infrastruttura {{site.data.keyword.cloud}}, cosa che avviene alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}. Alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}, che in genere è di 30 giorni, le sottoreti e le VLAN vengono eliminate e l'eliminazione dell'istanza viene completata.

Per l'istanza eliminata ti vengono addebitati costi fino alla fine del ciclo di fatturazione di {{site.data.keyword.cloud_notm}}.
{:note}

## Procedura per eliminare le istanze dalla pagina Risorse
{: #sd_deletinginstance-procedure1}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, trova l'istanza da eliminare.
3. Nella colonna **Azioni**, fai clic sull'icona Elimina.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Nella colonna **Azioni**, fai di nuovo clic sull'icona Elimina.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Procedura per eliminare le istanze dalla pagina dei dettagli dell'istanza
{: #sd_deletinginstance-procedure2}

1. Dalla console {{site.data.keyword.vmwaresolutions_short}}, fai clic su **Risorse** nel riquadro di navigazione a sinistra.
2. Nella tabella **Istanze Cloud Foundation**, fai clic sull'istanza da eliminare.
3. Fai clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   Lo stato dell'istanza viene modificato in **In fase di eliminazione**. Una volta che l'istanza è stata eliminata, i suoi componenti vengono rilasciati e il suo stato viene modificato in **Eliminato**.
4. Se vuoi rimuovere il record dell'istanza dalla console {{site.data.keyword.vmwaresolutions_short}}, completa la seguente procedura:
   1. Fai di nuovo clic sull'icona del menu di overflow accanto a **Console vCenter** e quindi su **Elimina istanza**.
   2. Nella finestra **Elimina istanza**, fai clic su **OK**.

## Link correlati
{: #sd_deletinginstance-related}

* [Eliminazione di istanze Cloud Foundation in una configurazione multisito](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Visualizzazione delle istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Espansione e contrazione della capacità per le istanze Cloud Foundation](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
* [Eliminazione di configurazioni multisito](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)
* [Come contattare il supporto IBM](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
