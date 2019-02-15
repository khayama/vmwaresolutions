---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

# Vue d'ensemble de l'architecture générale

Les informations suivantes fournissent davantage de détails sur l'architecture de réseau qui est utilisée dans cette architecture de référence. Elles comprennent les sections suivantes :
* Présentation de **VMware vCenter Server on {{site.data.keyword.cloud}}** – Décrit les points forts de la plateforme vCenter Server.
* **Présentation du réseau** – Fournit des informations sur les composants réseau qui sont utilisés dans cette architecture de référence :
  - **Mise en réseau d'{{site.data.keyword.cloud_notm}}** – {{site.data.keyword.cloud_notm}} fournit le réseau physique et est entièrement géré par {{site.data.keyword.cloud_notm}}. Passez en revue les caractéristiques principales de la mise en réseau d'{{site.data.keyword.cloud_notm}} pour appréhender les flots réseau entre l'environnement sur site et l'environnement hors site et entre les charges de travail qui sont hébergées dans différents services.
  - **NSX-V** – La mise en réseau de vCenter Server repose sur le réseau {{site.data.keyword.cloud_notm}} avec un réseau dissocié qui est fourni par VMware NSX-V. Ce réseau dissocié segmente le trafic à partir du réseau sous-jacent d'{{site.data.keyword.cloud_notm}} pour davantage de contrôle et de configurabilité incluant le mode BYOIP.
  - **{{site.data.keyword.containerlong_notm}}** - {{site.data.keyword.containerlong_notm}} utilise Calico comme plug-in d'interface CNI (Container Network Interface).
  - **{{site.data.keyword.icpfull_notm}}** - {{site.data.keyword.icpfull_notm}} utilise Calico comme plug-in d'interface CNI (Container Network Interface).

* **Intégration** – Décrit l'architecture des composants de mise en réseau permettant les flux de trafic réseau et l'adressage requis :
  - Affectation d'adresse IP
  - Flux de trafic réseau

## Présentation de vCenter Server

VMware vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle est un cloud privé hébergé qui vous permet de déployer rapidement et facilement votre infrastructure locale dans le cloud pour obtenir une hybridité d'infrastructure transparente et sécurisée et une véritable mobilité d'application.

vCenter Server Hybridity Bundle est déployé sur un minimum de quatre serveurs {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}, offre un stockage dédié via un réseau VSAN et inclut la configuration et le déploiement automatiques d'une infrastructure de mise en réseau définie par logiciel facile à gérer (NSX-V). vCenter Server Hybridity Bundle est une architecture de référence qui est déployée via l'automatisation, qui garantit la cohérence, des performances et la conformité. Dans de nombreux cas, vous pouvez mettre à disposition l'ensemble de l'environnement en moins d'une journée et l'infrastructure bare metal peut rapidement et de manière élastique augmenter ou diminuer la capacité de stockage et de calcul en fonction des besoins.

De nombreuses options sont disponibles pour améliorer et étendre vCenter Server Hybridity Bundle. Non seulement les offres de service {{site.data.keyword.cloud_notm}} incluent des options de stockage complémentaire et diverses options de connectivité WAN privées et publiques, mais elles couvrent également des domaines allant de la sécurité de plateforme, de la sécurité de réseau et de l'équilibrage de charge de trafic à la sauvegarde et à la reprise après incident.

Les services de sécurité de plateforme incluent HyTrust CloudControl on {{site.data.keyword.cloud_notm}}, qui fournit un support de conformité et de sécurité automatisé permettant une meilleure visibilité et un plus grand contrôle de votre environnement de cloud et de vos administrateurs. HyTrust DataControl on {{site.data.keyword.cloud_notm}} fournit une protection des données à l'aide d'un chiffrement puissant et d'une gestion de clés évolutive permettant de sécuriser vos charges de travail tout au long de leurs cycles de vie. {{site.data.keyword.cloud_notm}} Secure Virtualization simplifie la conformité et protège vos données via le chiffrement, des règles de géoprotection et des contrôles d'accès basé sur les rôles, tandis que KMIP for VMware on {{site.data.keyword.cloud_notm}} fournit une offre de gestion du cycle de vie des clés de chiffrement qui gère les clés de chiffrement utilisées par les services {{site.data.keyword.cloud_notm}} ou les applications créées par le client.

Les options de sécurité de réseau correspondent au service FortiGate Security Appliance on {{site.data.keyword.cloud_notm}}, qui met à disposition une paire de dispositifs FortiGate Security Appliance hautement disponibles afin d'analyser le trafic réseau et de protéger votre infrastructure virtuelle, et au service FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}, qui déploie une paire de machines virtuelles FortiGate hautement disponibles sur {{site.data.keyword.cloud_notm}} afin de réduire les risques en implémentant des contrôles de sécurité critiques au sein de votre infrastructure virtuelle. D'autres offres de sécurité de réseau sont en cours de développement.

L'offre de service d'équilibrage de charge de réseau F5 on {{site.data.keyword.cloud_notm}} optimise les performances et garantit la disponibilité et la sécurité de vos applications les plus vitales grâce à la suite F5 BIG-IP.

Les offres de sauvegarde et de reprise après incident fournies par IBM, Veeam et Zerto procurent une tranquillité d'esprit et une continuité opérationnelle en cas de panne. IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} est une solution de protection et de disponibilité des données pour des environnements virtuels. Veeam on {{site.data.keyword.cloud_notm}} active le concept d'Availability for the Always-On Enterprise™ avec un processus de sauvegarde, de reprise et de réplication intégré sur {{site.data.keyword.cloud_notm}}. Zerto on {{site.data.keyword.cloud_notm}} fournit aux clients locaux et {{site.data.keyword.cloud_notm}} une solution de reprise après incident sécurisée, flexible et évolutive.

vCenter Server Hybridity Bundle n'est pas un service géré, mais vous pouvez ajouter des services gérés par IBM si vous voulez décharger les opérations quotidiennes et la maintenance de la virtualisation, du système d'exploitation invité ou des couches application. L'équipe {{site.data.keyword.cloud_notm}} Professional Services est également disponible pour vous aider à accélérer votre transition vers le cloud en vous offrant des services de migration, d'implémentation, de planification et d'intégration.

Les options d'intégration de plateforme de vCenter Server Hybridity Bundle ne se limitent pas aux options disponibles à partir de VMware, telles que vRealize Suite ou vSphere with Operations Management, mais couvrent plusieurs offres de service {{site.data.keyword.cloud_notm}}, telles que [vCenter Server et {{site.data.keyword.containerlong_notm}}](/docs/services/vmwaresolutions/archiref/vcsiks/vcsiks-intro.html) et [vCenter Server et {{site.data.keyword.cloud_notm}} Private](/docs/services/vmwaresolutions/archiref/vcsicp/vcsicp-intro.html), qui utilisent open source Terraform pour gérer et fournir une infrastructure en tant que code.

Le portefeuille complet de services et d'offres d'intégration multi-offre disponible pour vCenter Server Hybridity Bundle fournit une plateforme véritablement hybride qui fait de l'hybridité un Service possible.

### Liens connexes

* [Présentation de vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs/vcs-hybridity-intro.html)