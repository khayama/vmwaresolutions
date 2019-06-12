---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-16"

---

# 主動作業
{: #opsprocs-proactive}

這些主動檢查的目標是讓系統管理者能夠維護 vCenter 伺服器環境處於性能狀態。每日執行時，應該會防止與使用率、容量及效能問題相關的許多一般問題，而不影響您的工作負載。這些主動檢查可以分類為下列結構：

* 性能 - 確認指出目前影響環境性能的問題，並需要立即注意，以將影響降到最低，亦即硬體故障。
* 風險 - 確認指出沒有立即威脅但應該在不久的未來會解決的問題，亦即容量問題。
* 效率 - 確認指出要改善效能或收回資源的區域。例如，正確調整虛擬機器 (VM) 及叢集大小。

其中許多主動作業都可以使用 Operations Management on {{site.data.keyword.cloud}} 進行更簡單的作業，並降低管理額外負擔。

運用使用率時，必須瞭解您的「基準線」。這個基準線反映您環境中的正常作業。根據所有用戶端的標準作法，所有用戶端都有不同的基準線（vCenter Server 實例上執行的工作負載等）。這些主動檢查接著會比較最新容量/效能/使用率與這個基準線。總言之，這些主動使用率檢查會回答 4 個問題：

1. 我現在是否過度使用？
2. 是否容量很快就不足？
3. 我的叢集在預期尖峰使用期間是否太小？
4. 是否可以收回虛擬基礎架構中的未用資源？

下列準則可協助您主動維護穩定環境：

* 針對您計劃執行的所有 VM 配置足夠的資源，來規劃 VM 部署。不要忘記容許 vSphere ESXi 本身的資源。
* 正確調整 VM 大小，並且只將該 VM 所需的虛擬資源數目配置給每個 VM。佈建超過所需資源的 VM，會降低相同主機上該 VM 及其他 VM 的效能。
* 一般而言，80% 的主機 CPU 使用率是合理的最高限值，而 90% 應該是 CPU 接近超載狀況的警告。如果主機接近 80% 的 CPU 使用率，則請佈建其他主機。
* 一般而言，80% 的主機 RAM 用量是合理的最高限值，而 90% 應該是完整利用主機的警告。如果主機接近 80% 的 RAM 用量，則請佈建其他主機。
* 很重要的是不要配置不足的記憶體，因此請配置足夠的記憶體來保留您要在 VM 中執行之應用程式的工作集，以將緩慢最小化。緩慢可能會明顯影響應用程式效能。不過，您也應該避免大幅過度配置記憶體。
* 只有在環境中需要時，才會使用資源設定、保留、共用及限制。如果您預期經常變更可用資源總計，則請使用共用（而非保留），在 VM 之間平均地配置資源。只有在資源競用時，共用才會生效。
* 如果您確實需要使用保留，則請將它們配置為指定可接受的 CPU 或記憶體數量下限，而不是您要使用的數量。
* 使用資源儲存區進行委派的資源管理，以及完整隔離資源儲存區，以將資源儲存區類型設為「固定」，並使用「保留」和「限制」。
* 將多層服務的 VM 分組至資源儲存區。這容許整體指派服務的資源。請小心選取 VM 的資源設定（亦即，保留、共用和限制）。設定保留太高，可能會在叢集中保留較少的未保留資源，因此會限制 DRS 必須平衡載入的選項。
* 設定限制太低，可能會讓 VM 無法使用叢集中可用的額外資源來改善其效能。
* 使用 VMware Update Manager，在執行未使用超過 80% 的叢集，以容許對主機進行補救的成功率更高。叢集補救最可能在完整使用叢集時成功。
* 精簡佈建儲存空間的原因很多，不過，精簡佈建會增加維護環境的管理工作負載，因為在容量管理處理程序中需要非常小心。
*  分析您的 VM 成長，並瞭解基礎架構的使用如何達到支援此成長的速度、訂購額外容量以加速此成長。
* 使用可使用的容量，這會考慮 HA/緩衝區等，而非規劃時的可用容量總計。
* 確定您執行系統可用 BIOS 的最新版本。
* 確定您執行已安裝產品的最新 VMware 更新項目，其中包括 VM 硬體及 VM Tools。

## 作業清單
{: #opsprocs-proactive-tasks}

表 1. 主動作業

| 標題 |說明       |
|---|---|
| 性能 | 使用 vCenter，檢查所有主機及 VM 物件的性能。有條不紊地逐步執行：叢集、主機、資料儲存庫、VM，以及警示的網路外觀。|
| 警示及通知檢查 | vCenter 中是否有任何您尚未收到通知的作用中警示？依預設，vCenter 具有一些在安裝時定義的警示。這些警示可以警告您發生問題，不過，依預設，它們在 vSphere 用戶端中不會採取警告或警示以外的動作。它們可以配置為通知，例如電子郵件。當您檢查主機及 VM 物件的性能時，請檢閱任何警示，以及決定是否需要通知，並視需要進行配置。您只需要收到最重要或嚴重問題的通知。請考量下列事項：我要在早上 2 點收到此問題的通知，還是可以等到正常工作時間，以及太多通知被視為「雜訊」，而人的本質會忽略所有警示。|
| 叢集 CPU 及記憶體容量/使用率檢查 | 使用 vCenter，依次導覽至每個叢集，並選取「監視」、「效能」，來檢閱叢集 CPU 及記憶體的容量/使用率度量值。請檢閱圖形及統計資料，以確保叢集有足夠的資源可滿足需求。需求應該是根據維護下列項目而來：足夠的容量，以讓 VM 在需要時進行快速寄發、供 vSphere ESXi 主機故障時使用，以及根據已知服務要求來新增 VM。|
| 資料儲存庫容量/使用率檢查 | 使用 vCenter，依次導覽至每個資料儲存庫，並選取「監視」、「效能」、「空間」，來檢閱資料儲存庫的容量/使用率度量值。請檢閱圖形及統計資料，以確保資料儲存庫有足夠的空間可滿足需求。需求應該是根據維護下列項目而來：足夠的容量，以供 vSphere ESXi 主機故障時使用（針對 vSAN 叢集），以及根據已知服務要求來新增 VM。|
| 資料儲存庫效能檢查 | 使用 vCenter，依次導覽至每個資料儲存庫，並選取「監視」、「效能」、「效能」、「即時」，來檢閱資料儲存庫的效能度量值。請檢閱圖形及統計資料，以確保預期有資料儲存庫效能基準線，且可以說明任何變更。請調查任何異常狀況。|
| 裸機伺服器韌體 | 最佳作法是為裸機伺服器主機安裝最新的韌體更新項目。請檢查裸機伺服器主機上的韌體更新項目，方法為依次導覽至每個主機位於 control.softlayer.com 的遠端管理頁面，然後選取 OS 重新載入。在顯示的頁面中，檢閱主機板和硬碟的「現行版本」和「更新版本」，並查看是否有可用的更新項目。若是如此，請規劃在下次維護時間更新韌體。如需相關資訊，請參閱[常見問題：裸機伺服器](/docs/bare-metal?topic=bare-metal-bm-faq#what-if-my-bare-metal-server-has-out-of-date-firmware){:new_window}。|
| vSphere ESXi 修補 | 如需檢查 vSphere ESXi 修補程式可用性的相關資訊，請參閱[建立基準線並連接至庫存物件](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines){:new_window}。|
| VM 硬體更新項目 | 如需檢查 VM 硬體更新項目可用性的相關資訊，請參閱[建立基準線並連接至庫存物件](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines){:new_window}。|
| VM Tools 更新項目 | 如需相關資訊，請參閱[建立基準線並連接至庫存物件](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-baselines#vum-baselines){:new_window}。|
| vSphere vSAN 修補 | 如需檢查 vSphere vSAN 修補程式可用性及修補處理程序的相關資訊，請參閱[更新 vSAN 叢集](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-updating-vsan#vum-updating-vsan){:new_window}。|
| vCenter 修補 |如需檢查 VCSA 修補程式可用性以及套用更新項目的相關資訊，請參閱 [VCSA 更新項目及 SSO 鏈結的 vCenter](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-updating-vcsa#vum-updating-vcsa){:new_window}。|
| 更新 NSX | 如需檢查 NSX 修補程式可用性以及套用升級的相關資訊，請參閱[NSX 修補](/docs/services/vmwaresolutions?topic=vmware-solutions-vum-updating-nsx#vum-updating-nsx){:new_window}。|
| 不使用 VM Tools 檢查 VM | 最佳作法是安裝 VM Tools，因為這容許與 OS 進行更大的互動，例如循序關閉 VM 的電源。您可以使用 vCenter 來檢查哪些 VM 未安裝 VM Tools，方法為導覽至叢集、選取「相關物件」、VM，然後是表格中啟用以執行 VM Tools 的直欄及 VM Tools 版本。請檢閱清單，並適當地安裝 VM Tools。|
| 具有 Snapshot 的 VM | 如需使用 Snapshot 時的最佳作法的相關資訊，請參閱[在 vSphere 環境中使用 Snapshot 的最佳作法 (1025279)](https://kb.vmware.com/s/article/1025279){:new_window}。識別具有 Snapshot 的 VM 是否存在很重要，因為使用單一 Snapshot 超過 72 小時會建立一個大小繼續增長的 Snapshot 檔案，並可能導致 Snapshot 儲存空間位置耗盡空間，並影響系統效能。若要檢閱具有 Snapshot 的 VM，請使用 Web Client 連接至 vCenter，並選取 vCenter Server，然後移至「相關物件」標籤。用滑鼠右鍵按一下直欄標題，然後移至「顯示/隱藏直欄」清單。從直欄清單中，選擇「需要合併」選項。這個直欄會顯示 Snapshot 上目前正在執行的所有 VM。|
| AD/DNS OS 修補 | Microsoft Active Directory (AD) / 網域名稱伺服器 (DNS) 自動設定為只下載更新。如需相關資訊，請參閱[其他限制及考量](/docs/services/vmwaresolutions?topic=vmware-solutions-trbl_limitations#trbl_limitations){:new_window}以進一步更新建議。|
| 檢查儲存空間延遲 | 檢查儲存空間延遲，以瞭解對 vSphere ESXi 主機存取資料儲存庫的任何變更。延遲太高會導致 VM 中管理的應用程式變慢。在 vCenter 中，導覽至每個資料儲存庫，並使用「效能」標籤檢閱每個 VM 的平均寫入延遲。|
| 檢閱具有虛擬裝置的 VM | 虛擬裝置（例如 CD 或軟碟機）會產生額外負擔，因此請移除 VM 不需要的任何裝置。|
| vSAN 容量建議 | 當叢集中的任何容量裝置達到 80% 滿時，vSAN 會自動重新平衡叢集，直到所有容量裝置上的可用空間低於臨界值為止。下列作業可能會導致磁碟容量達到 80% 並起始叢集重新平衡：硬體故障、使用「撤除所有資料」選項讓 vSAN 主機進入維護模式，或在主機上具有獲指派 PFTT=0 的物件時，使用「確保資料存取性」讓 vSAN 主機進入維護模式。若要提供足夠的空間來進行維護及重新保護，並將 vSAN 叢集中的自動重新平衡事件減到最少，請考慮隨時保留 30% 的可用容量。|
| 叢集使用率檢查 | 使用 vCenter，檢閱每個叢集，並識別哪些叢集的 CPU 及 RAM 使用率等於或大於 50%。已選擇 50% 作為警告層次，以聚焦於這個具有額外主機之叢集的潛在擴充或是新增叢集。50% 使用率與最大值 80% 到 90% 之間的差異，在於基於服務要求而需要的額外 VM 空間。達到 50% 的限制時，您應該在需要新增其他資源時，查看近期未來的要求和預測。|
| 叢集合併檢閱 | 使用 vCenter，檢閱每個叢集，並識別哪些叢集的 CPU 及 RAM 使用率等於或小於 30%。已選擇 30% 作為警告層次，以透過移除主機或移除此叢集並將 VM 移至另一個叢集，來聚焦於此叢集的正確大小調整。|
| 正確調整大小過大的 VM | 使用簡單的方法來正確調整大小過大的 VM；a. 識別、b. 側寫並調整以及 c. 監視需求趨勢。使用 vCenter 識別可能需要進行正確大小調整的大型 VM。導覽至「監視」、「效能」，以及側寫一段時間之工作負載的平均 CPU 和 RAM 需求設定檔，並調整虛擬資源。最後，繼續監視工作負載，以查看效能可接受。理想情況下，使用的 VM 的記憶體數量應該接近來賓 OS 所使用的記憶體，再加上執行 VM 的額外負擔。|
| 正確調整大小過小的 VM | 使用簡單的方法來正確調整大小過小的 VM；a. 識別、b. 側寫並調整以及 c. 監視需求趨勢。識別需要進行正確大小調整的小型 VM。側寫一段時間之工作負載的平均 CPU 和 RAM 需求設定檔，並調整虛擬資源。最後，繼續監視工作負載，以查看效能可接受。理想情況下，使用的 VM 的記憶體數量應該接近來賓 OS 所使用的記憶體，再加上執行 VM 的額外負擔。|
| 檢查 VM 硬體裝置相容性 | 使用通訊線資源上的 VMware 硬體相容性，檢查該 OS 是否支援 VM 硬體資源、網路、儲存裝置等。如果不予支援，則請變更為支援的裝置，以提高可靠性及效能。|

## 相關鏈結
{: #opsprocs-proactive-links}

* [Operations Management on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-opsmgmt-intro)