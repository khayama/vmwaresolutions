---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 新增、檢視及刪除 VMware Federal 實例的叢集

依預設，您訂購實例時所配置的 ESXi 伺服器會分組為 **cluster1**。

您可以將叢集新增至 VMware Federal 實例，以擴充運算及儲存空間容量。在叢集內，您可以管理 ESXi 伺服器，以進行更適當的資源配置及高可用性。不再需要時，您可以從實例刪除新增的叢集。

**可用性：**只有部署在（或升級至）2.3 版及更新版本的實例，才能使用新增及刪除叢集特性。

## 將叢集新增至 VMware Federal 實例

可新增至實例的叢集數目，取決於實例版本：
* 對於已部署在（或升級至）2.5 版及更新版本的實例，叢集、主機及 VM 數目決定您可新增的叢集數目上限。您必須遵守 VMware 大小準則及部署限制。
* 對於已部署在（或升級至）2.2 版及更新版本的實例，您最多可以新增 10 個叢集。

如需上限的相關資訊，請參閱 [VMware 配置上限](https://configmax.vmware.com/home){:new_window}。

### 系統設定

當您新增 VMware Federal 實例的叢集時，必須指定下列設定。

#### 叢集名稱

叢集名稱必須滿足下列需求：
* 只容許英數及橫線 (-) 字元。
* 叢集名稱的開頭及結尾必須是英數字元。
* 叢集名稱的長度上限為 30 個字元。
* 叢集名稱在 VMware Federal 實例內必須是唯一的。

#### 資料中心位置

依預設，叢集的資料中心會設為 VMware Federal 實例的資料中心。

### Bare Metal Server 設定

#### Skylake

指定 Bare Metal Server 的 CPU 型號及 RAM。可用的選項可能會根據一開始部署您實例所用的版本而不同。

表 1. Skylake {{site.data.keyword.baremetal_short}} 的選項

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Silver 4110 處理器/總計 16 核心，2.1 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器/總計 28 核心，2.2 GHz|64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 Processor / 總計 36 核心，2.3 GHz |64 GB、96 GB、128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Broadwell

指定 Bare Metal Server 的 CPU 型號及 RAM。可用的選項可能會根據一開始部署您實例所用的版本而不同。

表 2. Broadwell {{site.data.keyword.baremetal_short}} 的選項

| CPU 型號選項             |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 / 總計 16 核心，2.1 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 / 總計 24 核心，2.2 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 / 總計 28 核心，2.6 GHz |64 GB、128 GB、256 GB、512 GB、768 GB、1.5 TB |

#### Bare Metal Server 數目

一個叢集至少需要兩部 {{site.data.keyword.baremetal_short}}。

對於已部署在 2.3 版或更新版本的 VMware Federal 實例，您可以針對叢集新增最多 59 部 {{site.data.keyword.baremetal_short}}，並且一次可以新增 1 到 59 部 ESXi 伺服器。

部署之後，您最多可以另外建立四個叢集。對於 vSAN 儲存空間設定，起始叢集及部署後的叢集都需要四部伺服器。

### 儲存空間設定

儲存空間設定是根據您選取的 Bare Metal Server 配置及儲存空間類型而定。

#### vSAN 儲存空間

請指定下列 vSAN 選項：
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過所限制的 8 個容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。

  **高效能 Intel Optane** 選項僅適用於 Skylake CPU 型號「雙重 Intel Xeon Gold 5120」及「雙重 Intel Xeon Gold 6140」。
  {:note}

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。
* **vSAN 授權**：選取 VMware vSAN 6.6 授權版本（Advanced 或 Enterprise）。

如果起始叢集已新增為 vSAN 叢集，則任何其他 vSAN 叢集都使用相同的 vSAN 授權，且與起始 vSAN 叢集具有相同的配置。如果實例中的任何叢集都選擇在其上（起始或額外叢集）部署 vSAN，則也是這種情況。第一次新增叢集時，系統會提示您提供 vSAN 授權及版本。下次選取 vSAN 作為新的叢集時，就會重複使用您最初選擇的項目。

#### NFS 儲存空間

當您選取 **NFS 儲存空間**時，可以為所有共用使用相同設定的實例新增檔案層次共用儲存空間，也可以為每一個檔案共用指定不同的配置設定。請指定下列 NFS 選項：

檔案共用數目必須在 1 到 32 的範圍內。
{:note}

* **個別配置共用**：選取以為每一個檔案共用指定不同的配置設定。
* **共用數目**：為每一個檔案共用使用相同的配置設定時，請指定您要新增之 NFS 共用儲存空間的檔案共用數目。
* **大小**：選取符合共用儲存空間需求的容量。
* **效能**：根據您的工作負載需求，選取每 GB 的 IOPS（每秒輸入/輸出作業數）。
* **新增 NFS**：選取以新增要使用不同配置設定的個別檔案共用。

表 3. NFS 效能層次選項

|選項          |詳細資料      |
  |:------------- |:------------- |
  |2 IOPS/GB |這個選項是為大部分通用工作負載而設計。應用的範例包括：管理小型資料庫、備份 Web 應用程式，或是 Hypervisor 用的虛擬機器磁碟映像檔。|
  |4 IOPS/GB |這個選項是為一次擁有高百分比作用中資料的高密度工作負載而設計。應用的範例包括：交易式資料庫。|
  |10 IOPS/GB |這個選項是為要求最嚴苛的工作負載類型而設計，例如分析。應用的範例包括：高交易量資料庫，以及其他對效能敏感的資料庫。此效能層次限制為每個檔案共用的容量上限為 4 TB。|

### 授權設定

下列 VMware 元件的 {{site.data.keyword.IBM}} 提供的授權：

  * vSphere Enterprise Plus 6.5u1
  * vCenter Server 6.5
  * NSX Service Providers 6.4（Base、Advanced 或 Enterprise 版本）
  * （針對 vSAN 叢集）vSAN 6.6（Advanced 或 Enterprise 版本）

### 訂單摘要

根據您選取的叢集配置，預估成本會立即產生並顯示在**訂單摘要**右窗格中。

## 將叢集新增至 VMware Federal 實例的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要新增叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法將叢集新增至實例。{:note}
3. 按一下左導覽窗格上的**基礎架構**，然後按一下**叢集**表格右上角的**新增**。
4. 在**新增叢集**頁面上，輸入叢集名稱。
5. 針對 Bare Metal Server 配置，選取 **CPU 型號**、**RAM** 數量及 **Bare Metal Server 數目**。
6. 完成儲存空間配置。
  * 如果您選取 **vSAN 儲存空間**，請指定容量及快取磁碟的磁碟類型以及磁碟數目。如果您要更多儲存空間，請勾選**高效能 Intel Optane** 方框。
  * 如果您選取 **NFS 儲存空間**，而且要對所有檔案共用新增及配置相同的設定，請指定**共用數目**、**大小**及**效能**。
  * 如果您選取 **NFS 儲存空間**，而且要個別新增及配置檔案共用，請選取**個別配置共用**，然後按一下**新增 NFS** 標籤旁的 **+** 圖示，並針對每個個別檔案共用選取**大小**及**效能**。您必須至少選取一個檔案共用。
7. 選取授權配置的 VMware vSAN 授權版本。
8. 在**訂單摘要**窗格上，先驗證叢集配置，再新增叢集。
   1. 檢閱叢集的設定。
   2. 檢閱預估的叢集成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上角的**列印**或**下載**圖示。
   3. 按一下適用於您訂單的條款鏈結，並先確認您同意這些條款，再新增叢集。
   4. 按一下**佈建**。

## 將叢集新增至 VMware Federal 實例之後的結果

1. 會自動啟動叢集的部署，而且叢集的狀態變更為**正在起始設定**。您可以從實例摘要頁面檢視部署歷程，以檢查部署的狀態。
2. 叢集備妥可用時，其狀態會變更為**備妥使用**。新增的叢集已啟用「vSphere 高可用性 (HA)」及「vSphere 分散式資源排程器 (DRS)」。

您無法變更叢集名稱。變更叢集名稱可能會導致在叢集裡新增或移除 ESXi 伺服器的作業失敗。{:important}

## 在 VMware Federal 實例中檢視叢集的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下實例來檢視其中的叢集。
3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，檢視叢集的摘要：
   * **名稱**：叢集的名稱。
   * **ESXi 伺服器**：叢集裡的 ESXi 伺服器數目。
   * **CPU**：叢集裡 ESXi 伺服器的 CPU 規格。
   * **自訂 vSAN 磁碟**：叢集裡的 vSAN 磁碟數目（包括磁碟類型及容量）。
   * **記憶體**：叢集裡 ESXi 伺服器的記憶體大小總計。
   * **資料中心位置**：管理叢集所在的資料中心。
   * **Pod**：部署叢集的 Pod。
   * **狀態**：叢集的狀態。狀態可以具有下列其中一個值：
     <dl class="dl">
         <dt class="dt dlterm">正在起始設定</dt>
         <dd class="dd">正在建立及配置叢集。</dd>
         <dt class="dt dlterm">正在修改</dt>
         <dd class="dd">正在修改叢集。</dd>
         <dt class="dt dlterm">備妥使用</dt>
         <dd class="dd">叢集已備妥可供使用。</dd>
         <dt class="dt dlterm">正在刪除</dt>
         <dd class="dd">正在刪除叢集。</dd>
         <dt class="dt dlterm">已刪除</dt>
         <dd class="dd">已刪除叢集。</dd>
     </dl>
   * **動作**：按一下**刪除**圖示，以刪除叢集。
4. 按一下叢集名稱，以檢視 ESXi 伺服器、儲存空間及授權詳細資料。

### ESXi 伺服器

   * **名稱**：ESXi 伺服器的名稱格式為 `<host_prefix><n>.<subdomain_label>.<root_domain>`，其中：

      `host_prefix` 是主機名稱字首、`n` 是 ESXi 伺服器的序列、`subdomain_label` 是子網域標籤，而 `root_domain` 是根網域名稱。

   * **版本**：ESXi 伺服器的版本。
   * **認證**：用來存取 ESXi 伺服器的使用者名稱及密碼。
   * **專用 IP**：ESXi 伺服器的專用 IP 位址。
   * **狀態**：ESXi 伺服器的狀態，可以是下列其中一個值：
        <dl class="dl">
        <dt class="dt dlterm">已新增</dt>
        <dd class="dd">已新增 ESXi 伺服器，且已備妥可供使用。</dd>
        <dt class="dt dlterm">正在新增</dt>
        <dd class="dd">正在新增 ESXi 伺服器。</dd>
        <dt class="dt dlterm">正在刪除</dt>
        <dd class="dd">正在刪除 ESXi 伺服器。</dd>
        </dl>

### Storage

   * **名稱**：資料儲存庫名稱。
   * **大小**：儲存空間的容量。
   * **IOPS/GB**：儲存空間的效能層次。
   * **NFS/入口網站**：儲存空間的 NFS 版本。
   * **狀態**儲存空間的狀態，可以是下列其中一個值：
          <dl class="dl">
        <dt class="dt dlterm">已新增</dt>
        <dd class="dd">已新增 ESXi 伺服器，且已備妥可供使用。</dd>
        <dt class="dt dlterm">正在新增</dt>
        <dd class="dd">正在新增 ESXi 伺服器。</dd>
        <dt class="dt dlterm">正在刪除</dt>
        <dd class="dd">正在刪除 ESXi 伺服器。</dd>
        </dl>

### 授權

   * **授權**：授權類型。
   * **訂購類型**：授權由 IBM 提供或使用者提供。
   * **授權版本**：授權的版本。
   * **授權碼**：授權碼。
   * **總容量 (CPU)**：授權的 CPU 容量總計。
   * **可用容量 (CPU)**：授權的可用 CPU 容量。

## 從 VMware Federal 實例刪除叢集

不再需要叢集時，即可從實例刪除叢集。

使用此程序，以從部署在（或升級至）2.3 版及更新版本的實例移除叢集。
{:note}

### 刪除之前

* 使用此程序，從部署在 2.3 版或更新版本的實例刪除叢集。
* 對於部署在 2.2 版或更早版本實例的叢集，您必須將實例升級至 2.3 版，才能刪除您新增至實例的叢集。
* 您一次可以刪除單一叢集。若要刪除多個叢集，您必須依序執行它；請先等待刪除前一個叢集，再嘗試刪除下一個叢集。
* 在您刪除叢集之前，請確定叢集裡的所有節點都已開啟電源且正常運作。
* 當您刪除叢集時，也會一併刪除叢集裡的所有 VM（虛擬機器），且無法回復。如果您要保留 VM，請將它們移轉至其他叢集。
* 無法刪除預設叢集。

## 從 VMware Federal 實例刪除叢集的程序

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，按一下左導覽窗格中的**已部署的實例**。
2. 在 **vCenter Server 實例**表格中，按一下您要從中刪除叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法從實例刪除叢集。{:note}

3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，找出您要刪除的叢集，然後按一下**動作**直欄中的**刪除**圖示。

### 相關鏈結

* [檢視 VMware Federal 實例](/docs/services/vmwaresolutions/vcenter/vc_fed_viewinginstance.html)
* [擴充及縮減 VMware Federal 實例的容量](/docs/services/vmwaresolutions/vcenter/vc_fed_addingremovingservers.html)
