---

copyright:

  years:  2016

lastupdated: "2016-12-12"

subcollection: vmware-solutions


---

# Note sulla release per la V1.2
{: #relnotes_v12}

Questa release include nuove funzioni, miglioramenti dell'usabilità e correzioni di bug. Per un elenco di problemi risolti nelle diverse release, problemi noti con il prodotto e suggerimenti per l'utilizzo di {{site.data.keyword.vmwaresolutions_full}}, vedi [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}.

## Aggiornamenti dei componenti
{: #relnotes_v12-comp}

La nuova versione di VMware ESXi è vSphere 6.0 u2 p03, aggiornata da ESXi 6.0 u2 nella release precedente.

## Associazione degli account ID IBM e Bluemix
{: #relnotes_v12-ibm-id}

{{site.data.keyword.vmwaresolutions_full}} viene fornito come soluzione dell'infrastruttura nel catalogo IBM Bluemix®. Devi associare l'account **ID IBM** a un account Bluemix per utilizzare il tuo account **ID IBM** per accedere alla console {{site.data.keyword.vmwaresolutions_short}}.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Introduzione](/docs/services/vmwaresolutions?topic=vmware-solutions-getting-started)
* [Risoluzione dei problemi relativi all'accesso a Bluemix](/docs/account?topic=account-accessing){:new_window}

## Ripristino di emergenza Zerto
{: #relnotes_v12-zerto}

Puoi ordinare sia le istanze di VMware Cloud Foundation che di VMware vCenter Server con il ripristino di emergenza Zerto incluso al momento dell'ordine della tua istanza. Puoi anche aggiungere il ripristino di emergenza Zerto alle istanze esistenti di Cloud Foundation e vCenter Server nella pagina dei dettagli dell'istanza.

Per ulteriori informazioni, consulta i seguenti argomenti:
* [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [Visualizzazione delle istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_viewinginstances)
* [Ripristino di emergenza Zerto](/docs/services/vmwaresolutions/services?topic=vmware-solutions-addingzertodr)

## Informazioni sui prezzi
{: #relnotes_v12-price}

Ora puoi vedere ed esaminare il costo stimato della tua istanza ordinata prima di decidere di effettuare un ordine. Dopo aver selezionato i componenti durante l'ordine della tua istanza, il costo totale e i prezzi dettagliati di tutti i componenti sono visualizzati nella pagina **Riepilogo**.

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Miglioramenti al processo di ordine dell'istanza
{: #relnotes_v12-inst-order}

Il processo di ordine dell'istanza è stato notevolmente ottimizzato attraverso i seguenti miglioramenti:
* Sia per le istanze Cloud Foundation che per le istanze vCenter Server, sono in atto nuovi controlli di convalida per garantire che l'account utente SoftLayer® che utilizzi disponga delle autorizzazioni utente richieste, che lo spanning della VLAN sia abilitato e che venga fornita la chiave API corretta. Se alcuni requisiti non vengono soddisfatti, visualizzerai delle istruzioni direttamente sull'interfaccia utente per risolvere i problemi.
*  Per le istanze vCenter Server, l'ordine in cui selezioni i componenti dell'istanza è ottimizzato in modo che vengano visualizzati solo i data center che dispongono dell'hardware e dei server ESXi di cui hai bisogno. Questa modifica riduce la possibilità di successivi errori.

Per ulteriori informazioni, vedi [Ordine di istanze vCenter Server](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance).

## Notifiche e-mail aggiuntive
{: #relnotes_v12-email}

Ora ricevi una notifica via e-mail quando vengono aggiunti nuovi server ESXi alle tue istanze e quando vengono rimossi i server ESXi esistenti. Inoltre, ricevi una notifica via e-mail quando un'istanza viene eliminata. Le impostazioni di notifica sono abilitate per impostazione predefinita. In base alle tue preferenze, puoi impostare le notifiche che desideri ricevere nella pagina **Impostazioni**.

Per ulteriori informazioni, vedi [Account utente e impostazioni](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
