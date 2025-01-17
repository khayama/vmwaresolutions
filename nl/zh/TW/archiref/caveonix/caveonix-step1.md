---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-04"

subcollection: vmware-solutions


---

# 步驟 1 - 起始規劃及必要條件
{: #caveonix-step1}

每一個 Caveonix RiskForesight 應用程式元件都鬆散耦合，但集中管理。因此，可以用「全功能」虛擬機器 (VM) 部署模式來部署它們，或者，也可以將應用程式元件「橫向擴充」及部署在多部 VM 上，以獲得更高的可用性、效能及容量。

部署模式是基於可用性需求及資料保留的大小。RiskForesight 部署節點可描述如下：

-	基本 VM - 基本 VM 管理因資料保留而無法擴充的應用程式元件。這些元件包括：RiskForesight 使用者介面、RiskForesight 應用程式、RiskForesight 外掛程式、中央收集器、遠端收集器、索引資料儲存庫、傳訊資料儲存庫及關聯式資料儲存庫。
-	橫向擴充 VM - 橫向擴充 VM、資料庫和資料索引，根據「資產」的數目和所需的資料保留進行調整，資料保留會對橫向擴充硬碟空間及橫向擴充 VM 有更多的需求。

有三個 Caveonix RiskForesight 部署模型：

-	全功能 - 管理所有應用程式元件的單一 VM 的自動化部署及配置：
  - 在單一 VM 上安裝所有應用程式元件。
  - 遠端收集器可以安裝在個別的 VM 上。
  - 小型部署 - 最多 100 個資產（有 7 - 30 天的檢索）。
-	局部分散 - 自動化部署完成之後，您可以在起始 VM 中增加 RAM 及磁碟，並新增三部橫向擴充 VM，來手動橫向擴充。
  - 使用者介面、應用程式、外掛程式、中央收集器、遠端收集器、索引資料儲存庫、傳訊資料儲存庫及關聯式資料儲存庫部署在單一 VM 上。
  - 遠端收集器安裝在個別的 VM 上。
  -	索引資料節點部署在個別的 VM 上。
  -	中小型部署 - 最多 500 個資產（有 30 天的檢索）。
- 完全分散 - 根據資產數目和資料保留需求而新增額外的基本 VM 和橫向擴充 VM。
  - 應用程式元件分散至個別的 VM，以協助擴充。
  -	所需部署模式隨資產數目增加，範圍為 500 - 100,000。
  -	遠端收集器安裝在個別的 VM 上。
  -	使用者介面在多部 VM 上。
  -	應用程式和外掛程式在多部 VM 上。
  -	中央收集器配置在「叢集」中。
  -	關聯式資料儲存庫部署在主要 / 次要模型中。
  -	傳訊資料儲存庫部署在叢集中。
  -	索引資料儲存庫與主節點及資料節點一起部署。
  -	隨資產數目增加而使用更多資料節點來進行橫向擴充。

在任何 VM 部署之前，所有元件都必須具有 FQDN，並已登錄在 DNS 中。此步驟由 IBM Cloud for VMware Solutions 自動化針對起始「全功能」部署來完成，但擴充部署則是您的責任。

## 相關鏈結
{: #caveonix-step1-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
