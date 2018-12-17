---

copyright:

  years:  2016, 2018

lastupdated: "2018-11-16"

---

# Rete e infrastruttura di IBM Cloud

## VRF (Virtual Routing and Forwarding)
Gli account di {{site.data.keyword.cloud}} possono anche essere configurati come account VRF. Gli account VRF forniscono funzioni simili allo spanning della VLAN, abilitando l'instradamento automatico tra blocchi di IP della sottorete. Tutti gli account con connessioni Direct-Link devono essere convertiti o creati come account VRF.

## Direct Link
{{site.data.keyword.cloud_notm}} Direct Link Connect offre l'accesso privato alla tua infrastruttura {{site.data.keyword.cloud_notm}} e a qualsiasi altro cloud collegato al Network Service Provider tramite il tuo {{site.data.keyword.CloudDataCent_notm}} locale. Questa opzione è perfetta per la creazione della connettività multicloud in un unico ambiente. Connettiamo i clienti alla rete {{site.data.keyword.cloud_notm}} Private utilizzando una topologia di larghezza di banda condivisa. Come con tutti i prodotti Direct Link, puoi aggiungere l'instradamento globale, che abilita il traffico di rete privato a tutte le ubicazioni di {{site.data.keyword.cloud_notm}}.

## VPN (Virtual Private Network)

### VPN strongSwan
Il servizio VPN strongSwan IPSec fornisce un canale di comunicazione end-to-end sicuro su internet che si basa sulla suite di protocolli standard del settore Internet Protocol Security (IPSec).

### Hybridity (HCX)
VMware vCenter Server on {{site.data.keyword.cloud_notm}} Hybridity Bundle estende senza soluzione di continuità le reti dei data center in loco in {{site.data.keyword.cloud_notm}}, il che consente la migrazione delle macchine virtuali (VM) da e verso {{site.data.keyword.cloud_notm}} senza alcuna conversione o modifica.

## Struttura fisica

L'infrastruttura fisica richiesta per distribuire un cluster vCenter Server richiede la seguente specifica minima.

Tabella 1. Specifiche di vCenter Server

  | Distribuzione NFS | Distribuzione VSAN
---|---|---
Numero di server | 3 | 4
CPU | 28 core 2.2GHZ | 28 core 2,2GHZ
Memoria | 384 GB | 384 GB
Archiviazione|Gestione: 2 TB 2 IOPS, Carico di lavoro: 2 TB 4 IOPS|Min SSD: 960 GB(x2)   

Le opzioni di distribuzione IKS variano in base ai tuoi requisiti di nodo di lavoro.

Tabella 2. Specifiche IKS

  | Macchina virtuale (VM) | Bare Metal
--|---|--
Numero di server | 3 | 3
CPU | 2 – 56 core | 4 – 28 core
Memoria | 4 GB - 242 GB | 32 GB - 512 GB
Archiviazione | 100 GB |  SATA: 2 TB / SSD: 960 GB

## Struttura virtuale

Figura 1. Struttura fisica delle distribuzioni IKS e ICP

![Diagramma della struttura fisica delle distribuzioni IKS e ICP](vcsiks-phy-ics-iks-deployment.svg)

All'interno dell'istanza vCenter Server, le VM del cliente sono distribuite a DLR (Distributed Logical Router) e ESG (Edge Services Gateway) NSX dedicati.

L'ESG è configurato con una SNAT per consentire il traffico in uscita, consentendo la connettività internet per scaricare i prerequisiti ICP e la connettività a GitHub e Docker o può essere utilizzato un proxy web per fornire la connettività internet. L'ESG è configurato per accedere ai servizi DNS e NTP mediante la rete privata. L'integrazione all'istanza IKS è disponibile mediante la rete {{site.data.keyword.cloud_notm}} tra l'istanza vCenter Server e IKS.

## Componenti di vCenter Server

Figura 2. Componenti della piattaforma vCenter Server
![Diagramma dell'ambiente vCenter Server](vcsiks-vcs-env.svg)

### Controller servizio piattaforma
La distribuzione vCenter Server utilizza un singolo PSC (platform services controller)
esterno installato su una sottorete portatile nella VLAN privata associata alle VM di gestione. Il suo gateway predefinito è impostato sul BCR (backend customer router).

### vCenter Server
Come il PSC, vCenter Server viene distribuito come un dispositivo.
Inoltre, il vCenter viene installato su una sottorete portatile nella VLAN privata associata alle VM di gestione. Il suo
gateway predefinito è impostato sul BCR.

### NSX Manager
NSX Manager viene distribuito sul cluster vCenter Server iniziale. Inoltre,
a NSX Manager viene assegnato un indirizzo IP dal blocco di indirizzi portatile privato designato per i componenti di gestione.

### Controller NSX
L'automazione di {{site.data.keyword.cloud_notm}} distribuisce tre controller NSX all'interno del cluster iniziale. Ai controller vengono assegnati degli indirizzi IP dalla sottorete portatile privata designata per i componenti di gestione.

### NSX ESG / DLR
Vengono distribuite coppie di gateway dei servizi edge (ESG) NSX. In tutti i casi, una coppia di gateway viene utilizzata per il traffico in uscita dai componenti di automazione che risiedono sulla rete privata. Per vCenter Server e ICP, un secondo gateway noto come edge gestito da ICP, viene distribuito e configurato con un uplink alla rete pubblica e un'interfaccia che è assegnata alla rete privata. Tutti i componenti NSX necessari, come Distributed Logical Router (DLR), switch logici e firewall possono essere configurati dall'amministratore. Per ulteriori informazioni sugli edge NSX distribuiti come parte della soluzione, vedi la [Guida di rete di vCenter Server](../vcsnsxt/vcsnsxt-intro.html).

Le seguenti tabelle riepilogano le specifiche ESG / DLR ICP.

Tabella 3. Specifiche ESG ICP

Attributo  |  Specifica
--|--
Gateway servizio edge  |Dispositivo virtuale
Dimensione edge	Large |   Numero di vCPUs	2
Memoria	| 1 GB 
Disco	| 1000 GB sul datastore locale

Tabella 4. Specifiche DLR ICP

Attributo  |  Specifica
--|--|
Router logico distribuito |	Dispositivo virtuale
Dimensione edge	Compact | Numero di vCPUs	1
Memoria	| 512 MB
Disco	| 1000 GB sul datastore locale

## Componenti IKS

Figura 3. Componenti IKS
![Diagramma dei componenti IKS](vcsiks-iks-components.svg)

### Master Kubernetes

Il master Kubernetes è incaricato di gestire tutte le risorse di calcolo,
rete e archiviazione nel cluster. Il master Kubernetes garantisce che le tue
applicazioni e i tuoi servizi inseriti nel contenitore siano distribuiti equamente ai nodi di lavoro
nel cluster.

###	Nodo di lavoro
Ogni nodo di lavoro è una macchina fisica (bare metal) oppure una VM
che viene eseguita su hardware fisico nell'ambiente cloud. Quando esegui il provisioning di
un nodo di lavoro, determini le risorse che sono disponibili nei contenitori
ospitati su tale nodo di lavoro. Come dotazione standard, i tuoi nodi di lavoro sono configurati con un
Docker Engine gestito da IBM, risorse di calcolo separate, rete e un servizio volumi. Le funzioni di sicurezza integrate forniscono isolamento, funzionalità di gestione delle risorse e conformità di sicurezza dei nodi di lavoro.

### Link correlati

* [Panoramica di vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](../vcs/vcs-hybridity-intro.html)