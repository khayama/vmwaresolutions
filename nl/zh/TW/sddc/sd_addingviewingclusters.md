---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 新增、檢視及刪除 Cloud Foundation 實例的叢集
{: #sd_addingviewingclusters}

您在訂購實例時所配置的 ESXi 伺服器會依預設叢集進行分組。預設叢集名稱是：
* 對於已部署在 2.1 版或更新版本中的實例：**MGMT-Cluster-`<subdomain_label>`**
* 對於已部署在 2.0 版或更早版本中的實例：**SDDC-Cluster**

您可以將自己的叢集新增至 VMware Cloud Foundation 實例，以擴充運算及儲存空間容量。在叢集內，您可以管理 ESXi 伺服器，以進行更適當的資源配置及高可用性。不再需要時，您可以從實例刪除新增的叢集。

##  可用性       
{: #sd_addingviewingclusters-availability}

* 只有已部署在（或升級至）2.0 版及更新版本的實例，才能使用新增叢集特性。
* 只有部署在（或升級至）2.3 版及更新版本的實例，才能使用刪除叢集特性。  

## 將叢集新增至 Cloud Foundation 實例
{: #sd_addingviewingclusters-adding}

您最多可以將五個叢集新增至 Cloud Foundation 實例。

### 系統設定
{: #sd_addingviewingclusters-adding-sys-settings}

當您將叢集新增至 Cloud Foundation 實例時，必須指定下列設定。

#### 叢集名稱
{: #sd_addingviewingclusters-adding-cluster-name}

叢集名稱必須滿足下列需求：
* 只容許英數及橫線 (-) 字元。
* 叢集名稱的開頭及結尾必須是英數字元。
* 叢集名稱的長度上限為 30 個字元。
* 叢集名稱在 Cloud Foundation 實例內必須是唯一的。

#### 資料中心位置
{: #sd_addingviewingclusters-adding-dc-location}

依預設，叢集的 {{site.data.keyword.CloudDataCent}} 位置設為 Cloud Foundation 實例的 {{site.data.keyword.CloudDataCent_notm}}。您可以將叢集部署至不同於已部署實例的 {{site.data.keyword.CloudDataCent_notm}}，但您必須確定兩個 {{site.data.keyword.CloudDataCents_notm}} 之間的網路延遲少於 150 毫秒。若要檢查網路延遲，您可以使用 [SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} 之類的工具。

您可以使用的資料中心取決於針對部署所選取的 Bare Metal Server 配置。如果您選取 **Skylake** 或 **Broadwell** 配置，則也可以在選取的資料中心包含其他 Pod 時，將叢集部署至不同的 {{site.data.keyword.cloud_notm}} 基礎架構 Pod。部署起始實例的預設 {{site.data.keyword.cloud_notm}} 基礎架構 Pod 達到其容量上限時，此配置非常實用。

如果您將叢集部署至不同的資料中心或 Pod，則會訂購其他三個 VLAN，以與已訂購的 {{site.data.keyword.baremetal_short}} 搭配使用。

### Bare Metal Server 設定
{: #sd_addingviewingclusters-adding-bare-metal-settings}

您可以選擇 **Skylake** 或 **Broadwell**。

#### Skylake
{: #sd_addingviewingclusters-adding-skylake}

若為 **Skylake** 設定，您有數個選項可用於 **CPU 型號**和 **RAM**。可用的選項可能會根據一開始部署您實例所用的版本而不同。

表 1. Skylake {{site.data.keyword.baremetal_short}} 的選項

| CPU 型號選項        |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon Silver 4110 處理器 / 總計 16 核心，2.1 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 5120 處理器 / 總計 28 核心，2.2 GHz| 128 GB、192 GB、384 GB、768 GB、1.5 TB |
|雙重 Intel Xeon Gold 6140 處理器 / 總計 36 核心，2.3 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Broadwell
{: #sd_addingviewingclusters-adding-broadwell}

若為 **Broadwell** 設定，您有數個選項可用於 **CPU 型號**和 **RAM**。可用的選項可能會根據一開始部署您實例所用的版本而不同。

表 2. Broadwell {{site.data.keyword.baremetal_short}} 的選項

| CPU 型號選項        |RAM 選項          |
|:------------- |:------------- |
|雙重 Intel Xeon E5-2620 v4 / 總計 16 核心，2.1 GHz |128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2650 v4 / 總計 24 核心，2.2 GHz |128 GB、256 GB、512 GB、768 GB、1.5 TB |
|雙重 Intel Xeon E5-2690 v4 / 總計 28 核心，2.6 GHz |128 GB、256 GB、512 GB、768 GB、1.5 TB |
|四重 Intel Xeon E7-4820 v4 / 總計 40 核心，1.9 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
|四重 Intel Xeon E7-4850 v4 / 總計 64 核心，2.2 GHz |128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

### vSAN 儲存空間設定
{: #sd_addingviewingclusters-adding-vsan-storage-settings}

若為 **Skylake** 和 **Broadwell** Bare Metal Server 配置，您可以指定下列設定，以自訂 vSAN 儲存空間：
* **vSAN 容量磁碟的磁碟類型及大小**：選取所需容量磁碟的選項。
* **vSAN 容量磁碟數目**：指定您要新增的容量磁碟數目。
* 如果您要新增超過所限制的 8 個容量磁碟，請勾選**高效能 Intel Optane** 方框。這個選項提供 2 個額外容量磁碟機槽來放置共 10 個容量磁碟，並且適用於需要較少延遲且較高 IOPS 傳輸量的工作負載。

  **高效能 Intel Optane** 選項僅適用於 Skylake CPU 型號「雙重 Intel Xeon Gold 5120」及「雙重 Intel Xeon Gold 6140」。
  {:note}

* 檢閱 **vSAN 快取磁碟的磁碟類型**及 **vSAN 快取磁碟數目**值。這些值取決於您是否已勾選**高效能 Intel Optane** 方框。

### 授權設定
{: #sd_addingviewingclusters-adding-licensing-settings}

您可以在叢集裡指定 VMware 元件的授權選項（包括 VMware vSphere 及 VMware vSAN）：
* 對於「IBM 事業夥伴」使用者，包括 vSphere 授權（Enterprise Plus 版本）及 vSAN 授權，並可代表您購買。不過，您必須指定 vSAN 授權的版本。
* 對於不是「IBM 事業夥伴」的使用者，您可以選取**購買隨附**以將 IBM 提供的 VMware 授權用於這些元件，也可以選取**我將提供**並輸入自己的授權碼以針對元件「自帶授權 (BYOL)」。

## 將叢集新增至 Cloud Foundation 實例的程序
{: #sd_addingviewingclusters-adding-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要新增叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法將叢集新增至實例。
   {:note}

3. 按一下左導覽窗格上的**基礎架構**，然後按一下**叢集**表格右上方的**新增**。
4. 在**新增叢集**頁面上，輸入叢集名稱。
5. 如果您要在與實例管理所在不同的 {{site.data.keyword.CloudDataCent_notm}} 中管理叢集，請勾選 **Bare Metal Server** 下的**選取不同的位置**勾選框，然後選擇 {{site.data.keyword.CloudDataCent_notm}} 來管理實例。
6. 指定 **CPU 模型**及 **RAM** 大小，以完成「裸機」配置。
7. 完成儲存空間配置：
   1. 指定 vSAN 容量及快取磁碟的磁碟類型，以及磁碟數目。
   2. 如果您想要更多儲存空間，請選取 **Intel Optane 的高效能**勾選框。
8. 指定如何提供您的授權碼：
   * 對於「IBM 事業夥伴」使用者，包括 vSphere 授權（Enterprise Plus 版本）及 vSAN 授權，並可代表您購買。不過，您必須指定 vSAN 授權的版本。
   * 對於非「IBM 事業夥伴」的使用者，您可以選取下列其中一個選項：
       * 如果您想要我們代表您購買新授權，請針對元件選取**購買隨附**。對於 VMware vSAN，也請選取授權版本。
       * 如果您想要對元件使用您自己的 VMware 授權，請選取**我將提供**，並輸入該元件的授權碼。
9. 在**訂單摘要**窗格上，先驗證叢集配置，再新增叢集。
   1. 檢閱叢集的設定。
   2. 檢閱預估的叢集成本。按一下**定價詳細資料**以產生 PDF 摘要。若要儲存或列印訂單摘要，請按一下 PDF 視窗右上方的**列印**或**下載**圖示。
   3. 按一下適用於您訂單的條款鏈結，並先確認您同意這些條款，再新增叢集。
   4. 按一下**佈建**。

### 將叢集新增至 Cloud Foundation 實例之後的結果
{: #sd_addingviewingclusters-adding-results}

1. 會自動啟動叢集的部署，而且叢集的狀態變更為**正在起始設定**。您可以在實例摘要頁面上檢視部署歷程，以檢查部署的狀態。
2. 叢集備妥可用時，其狀態會變更為**備妥使用**。新增的叢集已啟用「vSphere 高可用性 (HA)」及「vSphere 分散式資源排程器 (DRS)」。

您不能變更叢集名稱。變更叢集名稱可能會導致在叢集裡新增或移除 ESXi 伺服器的作業失敗。
{:important}

## 在 Cloud Foundation 實例中檢視叢集的程序
{: #sd_addingviewingclusters-viewing-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **Cloud Foundation 實例**表格中，按一下實例來檢視其中的叢集。
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
4. 按一下叢集名稱，以檢視 ESXi 伺服器清單及其資訊：

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
   * vSAN 授權及 vSphere 授權的詳細資料。只有在您選擇於訂購叢集時使用自己的 VMware 授權 (BYOL) 時，才能使用 vSphere 授權詳細資料。
       * **授權類型**：vSAN 授權或 vSphere 授權。
       * **訂單類型**：授權由使用者所提供 (BYOL)，或代表使用者購買授權。
       * **授權版本**：授權的版本。
       * **授權碼**：授權碼。
       * **總容量 (CPU)**：授權所提供的總容量或 CPU 數目。
       * **可用容量 (CPU)**：授權中可用的容量。

## 從 Cloud Foundation 實例刪除叢集
{: #sd_addingviewingclusters-deleting}

不再需要叢集時，即可從實例刪除叢集。

### 刪除之前
{: #sd_addingviewingclusters-deleting-prereq}

* 使用此程序，從部署在 2.3 版或更新版本的實例刪除叢集。
* 對於部署在 2.2 版或更早版本實例的叢集，您必須將實例升級至 2.3 版，才能刪除您新增至實例的叢集。
* 您一次可以刪除單一叢集。若要刪除多個叢集，您必須依序執行它；請先等待刪除前一個叢集，再嘗試刪除下一個叢集。
* 在您刪除叢集之前，請確定叢集裡的所有節點都已開啟電源且正常運作。
* 當您刪除叢集時，也會一併刪除叢集裡的所有 VM（虛擬機器），且無法回復。如果您要保留 VM，請將它們移轉至其他叢集。
* 無法刪除預設叢集。

## 從 Cloud Foundation 實例刪除叢集的程序
{: #sd_addingviewingclusters-deleting-procedure}

1. 從 {{site.data.keyword.vmwaresolutions_short}} 主控台中，按一下左導覽窗格中的**資源**。
2. 在 **Cloud Foundation 實例**表格中，按一下您要從中刪除叢集的實例。

   請確定實例處於**備妥使用**狀態。否則，您無法從實例刪除叢集。
   {:note}

3. 在左導覽窗格上，按一下**基礎架構**。在**叢集**表格中，找出您要刪除的叢集，然後按一下**刪除**圖示。
4. 確認您已完成將 VM 移轉至其他叢集（適當的話），以及您要刪除叢集。

## 相關鏈結
{: #sd_addingviewingclusters-related}

* [檢視 Cloud Foundation 實例](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [擴充及縮減 Cloud Foundation 實例的容量](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
