---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---
# Preparazione dell'ambiente di installazione
{: #hcx-archi-prep-install}

L'installazione di VMware HCX on IBM Cloud ha i seguenti requisiti software:
* vSphere 5.5 U3 o vSphere 6.0u2 o superiore.
* Se viene utilizzato NSX, la versione 6.2.2 o superiore. NSX è obbligatorio per la migrazione della politica.
* Per utilizzare il vMotion tra cloud, si applicano le stesse limitazioni dell'affinità tra i cloud come se fossero in loco. Per ulteriori informazioni, consulta [VMware EVC and CPU Compatibility FAQ](https://kb.vmware.com/s/article/1005764).

## Configurazione della connettività di rete
{: #hcx-archi-prep-install-config-net}

HCX deve attraversare internet pubblico e le linee private e connettersi ai componenti del data center, come ad esempio le reti, gli switch e i gruppi di porte.
* [Requisiti di accesso alla porta](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-port-req) elenca le porte che devono essere aperte in modo che i dispositivi virtuali HCX possano essere installati correttamente.
* Sia l'ambiente vSphere in loco che l'ambiente cloud VCS HCX devono consentire la sincronizzazione dell'orologio NTP (Network Time Protocol) con i dispositivi in loco vSphere e i dispositivi VCS HCX. La porta UDP 123 deve essere accessibile alle reti e ai dispositivi virtuali HCX.

## Ambiente in loco
{: #hcx-archi-prep-install-on-prem-env}

Prima di installare HCX, verifica che il tuo ambiente possa supportare le attività che desideri eseguire. L'ambiente in loco deve supportare le seguenti attività prima che possa essere installato HCX.
* Virtual Center con vSphere 5.5 Aggiornamento 3 o 6.0 Aggiornamento 2.
* Le funzioni di migrazione della politica e vMotion richiedono NSX versione 6.2.2 o superiore.
* Un account del servizio vSphere con il ruolo di sistema di amministratore vCenter Server assegnato.
* Nel vCenter, lo spazio disco necessario per l'installazione dei dispositivi HCX.
* Indirizzi IP sufficienti per le VM in loco di cui è stato eseguito il provisioning durante l'installazione.
* Porte e firewall aperti come richiesto e documentato nei requisiti di accesso alla porta.
* Se il server SSO (single sign-on) è remoto, devono essere identificati l'URL del vCenter, il server SSO esterno o il PSC (Platform Services Controller) che esegue il servizio di ricerca esterno. Quando l'HCX Manager viene registrato con il vCenter, deve essere fornito questo URL.
* Se un vCenter non dispone di una propria istanza interna del servizio di ricerca, potrebbe essere per uno dei seguenti motivi:
  * vCenter 6.0u2 esegue un PSC (Platform Services Controller) esterno.
  * Il vCenter è nella modalità di collegamento (in cui il vCenter secondario utilizza il servizio SSO dal vCenter primario o da un servizio SSO esterno).

## Verifica dell'ambiente di installazione di livello 2
{: #hcx-archi-prep-install-verify-layer-2-inst}

L'estensione della rete di livello 2 ha i seguenti requisiti:
* Un vSphere Enterprise Plus Edition.
* Il vSphere vCenter deve soddisfare i seguenti requisiti per supportare l'estensione di livello 2:
  * Licenza di vSphere Enterprise Plus
  * È necessario un vDS (vSphere Distributed Switch). Lo switch distribuito è disponibile con vSphere Enterprise Plus Edition.
  * Quando installato, il dispositivo del servizio del concentratore di livello 2 in loco deve avere accesso a una porta vNIC e a tutte le VLAN per essere esteso.
  * Se la rete deve essere estesa su internet pubblico o su una VPN (su un percorso alternativo), la VM (Virtual Machine) L2C in VCS richiede un indirizzo IP. L'indirizzo IP remoto è obbligatorio per configurare il concentratore di livello 2.
  * Se vuoi più concentratori di livello 2, ognuno di essi deve avere un indirizzo IP in loco e nel cloud.

## Link correlati
{: #hcx-archi-prep-install-related}

* [Installazione e configurazione dell'HCX sull'origine](/docs/services/vmwaresolutions/archiref/hcx-archi?topic=vmware-solutions-hcx-archi-install-cfg-src)
* [VMware EVC and CPU Compatibility FAQ](https://kb.vmware.com/s/article/1005764)
