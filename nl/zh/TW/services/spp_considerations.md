---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# IBM Spectrum Protect Plus on IBM Cloud 概觀
{: #spp_considerations}

{{site.data.keyword.IBM}} Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務提供有效且可調式解決方案，以進行虛擬環境的資料保護、資料重複使用及資料回復。您可以將服務當成獨立式解決方案來實作，或與 IBM Spectrum Protect 環境整合以卸載副本，進行長期儲存及資料控管。

只有執行 vSphere 6.5 以及部署在（或升級至）2.2 版或更新版本的實例，才能使用此服務。目前安裝的 {{site.data.keyword.IBM}} Spectrum Protect Plus 版本是 10.1.3 版。
{:note}

## IBM Spectrum Protect Plus on IBM Cloud 的技術規格
{: #spp_considerations-specs}

下列元件已訂購並包括在 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務中：

### vCenter 資源
{: #spp_considerations-vcenter}

* 執行 IBM Spectrum Protect Plus 伺服器的伺服器 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 作業系統
   * 4 x 2.0 GHz 核心
   * 32 GB RAM
   * 370 GB 磁碟
* 執行 IBM Spectrum Protect Plus vSnap 伺服器及 VADP Proxy 的次要 VM
   * Linux 3.10.0-693.11.1.el7.x86_64 作業系統
   * 根據選取的儲存空間大小及 [IBM Spectrum Protect Plus 藍圖](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)大小指引所配置的 CPU 及 RAM
   * 150 GB 磁碟

### 用於備份的儲存空間
{: #spp_considerations-backup-storage}

使用下列選項之備份的可自訂儲存空間：
* 檔案儲存空間數目：1 - 10
* 每一個耐久性檔案儲存空間：500、1000、2000、4000、8000 或 12000 GB
* 儲存空間效能：0.25、2 或 4 IOPS/GB

請參閱 [IBM Spectrum Protect Plus 藍圖及調整大小工具](https://www.ibm.com/developerworks/community/wikis/home?lang=en#!/wiki/Tivoli%20Storage%20Manager/page/IBM%20Spectrum%20Protect%20Plus%20Blueprints)，以取得規劃及調整大小的相關資訊。

### 用於管理的儲存空間
{: #spp_considerations-mgmt-storage}

一個 1000 GB、2 個 IOPS/GB 耐久性檔案儲存空間，可管理 IBM Spectrum Protect Plus 虛擬機器，並在與備份儲存空間相同的子網路上執行。

### 網路
{: #spp_considerations-network}

兩個可攜式專用 IP 位址。

### 授權及費用
{: #spp_considerations-license}

* IBM Spectrum Protect Plus（10 到最多 1000 份 VM 授權，增量為 10）
* 透過 {{site.data.keyword.vmwaresolutions_short}} 主控台或當作 BYOL 所提供的 IBM Spectrum Protect Plus 授權（VM 數目，10 個套件）

## 安裝 IBM Spectrum Protect Plus on IBM Cloud 時的考量
{: #spp_considerations-install}

請先檢閱下列考量，再安裝 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務。

* 確定實例預設叢集裡的 CPU 及記憶體足夠用於 IBM Spectrum Protect Plus 虛擬機器。
* 根據 ESXi 伺服器的版本，確定 ESXi 伺服器上可用的 NFS 裝載足夠。

  在 VMware 中，部署在或升級至 2.2 版或更新版本的實例具有 `NFS.MaxVolumes` 參數設定。此參數定義 ESXi 伺服器的 NFS 裝載數目上限，而且可以設為 ESXi 伺服器版本特有的上限 256。如需相關資訊，請參閱 [Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239)。

  在實例預設叢集的每一部 ESXi 伺服器上，IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務最多會使用 11 個 NFS 磁區。此外，此服務還會建立暫時性 NFS 裝載來進行備份及還原。因此，您必須將 NFS 裝載數目設為至少 64，確保服務可以順利安裝及運作。

## 移除 IBM Spectrum Protect Plus on IBM Cloud 時的考量
{: #spp_considerations-remove}

請先檢閱下列考量，再移除 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 服務：
* 確定已移除所有備份工作配置以及作用中備份或還原作業。
* 當您移除此服務時，會從 IBM Spectrum Protect Plus VM 移除備份儲存庫的儲存空間，並取消儲存空間訂單，以永久地刪除備份儲存庫資料。
* 當您移除此服務時，也會移除針對此服務所訂購的備份儲存空間。在移除服務期間，所有備份都會變成無法存取。

## 相關鏈結
{: #spp_considerations-related}

* [IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}} 預防性服務規劃](https://www-01.ibm.com/support/docview.wss?uid=swg22012650){:new_window}
* [管理 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingspp)
* [訂購 IBM Spectrum Protect Plus on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-spp_ordering)
* [IBM Spectrum Protect Plus 文件](https://www.ibm.com/support/knowledgecenter/en/SSNQFQ/landing/welcome_ssnqfq.html)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
