---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation 概觀
{: #sd_cloudfoundationoverview}

VMware Cloud Foundation on {{site.data.keyword.cloud}} 的基礎部署包含四個 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}，其中已預先安裝 VMware Cloud Foundation 堆疊，並配置為提供統一的軟體定義資料中心 (SDDC) 平台。Cloud Foundation 原本便整合了 VMware vSphere、VMware NSX、VMware Virtual SAN，並且是根據 VMware 驗證的設計進行架構。

## Cloud Foundation 架構
{: #sd_cloudfoundationoverview-archi}

下圖說明 Cloud Foundation 部署的整體架構及元件。

圖 1. Cloud Foundation 架構

![Cloud Foundation 架構](sd_architecture.svg "Cloud Foundation 架構")

### 實體基礎架構
{: #sd_cloudfoundationoverview-physical-infras}

這層提供要供虛擬基礎架構使用的實體基礎架構（運算、儲存空間及網路資源）。

### 虛擬化基礎架構（運算、儲存空間及網路）
{: #sd_cloudfoundationoverview-virtualization-infras}

這層透過不同的 VMware 產品來將實體基礎架構虛擬化：
* VMware vSphere 將實體運算資源虛擬化。
* VMware Virtual SAN (vSAN) 會根據實體伺服器中的儲存空間來提供軟體定義的共用儲存空間。
* VMware NSX 是提供邏輯網路元件及虛擬網路的網路虛擬化平台。

### 虛擬化管理
{: #sd_cloudfoundationoverview-virtualization-mgmt}

這層包含 vCenter Server，它代表虛擬化環境的管理層。您可以使用相同的熟悉 vSphere API 相容工具及 Script，來管理 IBM 管理的 VMware 環境。

在 {{site.data.keyword.vmwaresolutions_short}} 主控台上，您可以使用新增及移除 ESXi 伺服器功能，來擴充及縮減實例的容量。此外，還可以使用在受管理環境中套用更新及升級 VMware 元件這類的生命週期管理功能。

如需架構的相關資訊，請參閱[解決方案概觀](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_overview)。

## Cloud Foundation 實例的技術規格
{: #sd_cloudfoundationoverview-specs}

Cloud Foundation 實例中包括下列元件。

硬體、網路、虛擬機器及儲存空間所產生的費用，可能會根據選取以用於部署的 {{site.data.keyword.CloudDataCent_notm}} 而有所不同。
{:note}

### Bare Metal Server
{: #sd_cloudfoundationoverview-bare-metal}

您的實例可以具有附有下列其中一個配置的 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}：
*  **Skylake**：2-CPU Intel Skylake 產生伺服器（Intel Xeon 4100/5100/6100 系列），搭配您選取的 CPU 型號及 RAM 大小。   
*  **Broadwell**：2-CPU Intel Broadwell 產生伺服器（Intel Xeon E5-2600/E7-4800 系列），搭配您選取的 CPU 型號及 RAM 大小。

如果您計劃使用 vSAN 儲存空間，則配置需要四個 {{site.data.keyword.baremetal_short}}。
{:note}

### 網路
{: #sd_cloudfoundationoverview-networking}

您的實例包含下列網路元件：
* 10 Gbps 雙重公用及專用網路上行鏈路
* 三個 VLAN（虛擬 LAN）：一個公用 VLAN 和兩個專用 VLAN
* 用於出埠 HTTPS 管理資料流量的安全管理服務 VMware NSX Edge Services Gateway (ESG)，其由 IBM 部署為管理網路拓撲的一部分。IBM 管理虛擬機器會利用此 ESG，來和與自動化相關的特定外部 IBM 管理元件進行通訊。如需相關資訊，請參閱[管理服務 NSX Edge 是否有安全風險？](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq#does-the-management-services-nsx-edge-pose-a-security-risk-)

  您無法存取此 ESG，因此無法使用它。如果您修改它，則可能無法從 {{site.data.keyword.vmwaresolutions_short}} 主控台管理 Cloud Foundation 實例。此外，使用防火牆或停用與外部 IBM 管理元件的 ESG 通訊，將導致 {{site.data.keyword.vmwaresolutions_short}} 變成無法使用。
  {:important}

* 如果您有現有叢集，並且其中具有現行 VMware vSphere 版本所支援的 ESXi 伺服器，則會自動啟用 EVC（加強型 vMotion 相容性）特性。EVC 提供叢集裡所有 ESXi 伺服器的 vMotion 相容性，方法是確保叢集裡的所有 ESXi 伺服器都向虛擬機器公開一組相同的 CPU 特性。透過使用 EVC，即使 ESXi 伺服器上的實際 CPU 可能不同，虛擬機器還是可以在叢集的任何 ESXi 伺服器之間移轉。

### 虛擬伺服器實例
{: #sd_cloudfoundationoverview-vsi}

您的實例具有下列 VSI（虛擬伺服器實例）：
* Microsoft Active Directory (AD) 及「網域名稱系統 (DNS)」服務的 VSI。多站台配置支援需要 VSI。此 VSI 規格為：Windows 2012 R2（8 GB RAM/2 個 CPU 核心/100 GB 磁碟/雙重 1 Gbps 專用上行鏈路）。
* IBM CloudBuilder 的 VSI，在完成實例部署之後會關閉它。
* （如果已訂購 Veeam on {{site.data.keyword.cloud_notm}}）已訂購 Veeam 備份服務的 VSI。

### Storage
{: #sd_cloudfoundationoverview-storage}

視選取的{{site.data.keyword.baremetal_short}}配置而定，您的實例可以具有下列儲存空間：
* 兩個 1 TB 的 SATA 開機磁碟
* 兩個 960 GB 的 SSD（固態磁碟）快取磁碟
* 一個 RAID 磁碟控制器
* 僅針對 **Skylake** 和 **Broadwell** 配置，您可以根據需求來設定磁碟機數目以及磁碟類型和容量。同時，您也具有「高效能 Intel Optane」選項，可提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟。「高效能 Intel Optane」選項取決於 CPU 型號。

### 授權（IBM 提供或 BOYL）與費用
{: #sd_cloudfoundationoverview-license-and-fee}

* 四個 VMware vSphere Enterprise Plus 6.5u1
* 四個 VMware vCenter Server 6.5
* 四個 VMware NSX Enterprise 6.3
* 四個 VMware vSAN Advanced 或 Enterprise 6.6
* 四個 SDDC Manager 授權（僅限 IBM 所提供）
* 四筆支援與服務費用

## Cloud Foundation 擴充節點的技術規格
{: #sd_cloudfoundationoverview-expansion-node-specs}

每個 Cloud Foundation 擴充節點會部署下列元件，並在您的 {{site.data.keyword.cloud_notm}} 帳戶中收取其費用。

### 擴充節點的硬體
{: #sd_cloudfoundationoverview-expansion-node-hardware}

一部具有 [Cloud Foundation 實例的技術規格](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview#technical-specifications-for-cloud-foundation-instances)中所呈現之配置的 {{site.data.keyword.cloud_notm}} Bare Metal Server。

### 擴充節點的授權與費用
{: #sd_cloudfoundationoverview-expansion-node-license-and-fee}

* 一個 VMware vSphere Enterprise Plus 6.5u1
* 一個 VMware vCenter Server 6.5
* 一個 VMware NSX Enterprise 6.3
* 一個 VMware vSAN Advanced 或 Enterprise 6.6
* 一個 SDDC Manager 授權
* 一筆支援與服務費用

您只能從 {{site.data.keyword.vmwaresolutions_short}} 主控台，而不能從 {{site.data.keyword.slportal}} 或透過主控台以外的任何其他方法，來管理在 {{site.data.keyword.cloud_notm}} 帳戶中建立的 {{site.data.keyword.vmwaresolutions_short}} 元件。如果您在 {{site.data.keyword.vmwaresolutions_short}} 主控台以外變更這些元件，則變更不會與主控台同步。
{:important}

**警告：**從 {{site.data.keyword.vmwaresolutions_short}} 主控台以外管理已在訂購實例時安裝至 {{site.data.keyword.cloud_notm}} 帳戶的所有 {{site.data.keyword.vmwaresolutions_short}} 元件，可能會讓您的環境不穩定。這些管理活動包括：
*  新增、修改、退回或移除元件
*  透過新增或移除 ESXi 伺服器來擴充或縮減實例容量
*  關閉元件電源
*  重新啟動服務

   這些活動的例外包括從 {{site.data.keyword.slportal}} 管理共用儲存空間檔案共用。這類活動包括：訂購、刪除（這可能會影響已裝載的資料儲存庫）、授權及裝載共用儲存空間檔案共用。

## 相關鏈結
{: #sd_cloudfoundationoverview-related}

* [Cloud Foundation 軟體資料清單](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_bom)
* [VMware vSphere 文件中心](https://pubs.vmware.com/vsphere-60/index.jsp){:new_window}
* [VMware NSX 6 文件中心](https://pubs.vmware.com/NSX-6/index.jsp){:new_window}
* [EVC 及 CPU 相容性常見問題](https://kb.vmware.com/s/article/1005764)
