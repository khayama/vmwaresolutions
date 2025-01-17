---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-01"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# 關於 ESXi 伺服器的常見問題
{: #faq_esxi}

尋找在 {{site.data.keyword.vmwaresolutions_full}} 主控台上管理的 ESXi 伺服器之相關常見問題的回答。

## 我可以新增多少部 ESXi 伺服器至實例中？
{: #faq_esxi-instance}
{: faq}

您的 vCenter Server 實例容許您將預設叢集擴充為具有多達 51 部 ESXi 伺服器。每一個非預設叢集可以擴充為具有多達 59 部 ESXi 伺服器。由於您最多可以將 10 個叢集新增至實例中，因此每一個已部署的實例在所有叢集裡最多可以有 51 + 9x59 = 582 部 ESXi 伺服器。

## 我可以新增多少部 ESXi 伺服器至叢集？
{: #faq_esxi-cluster}
{: faq}

如果是部署在 2.2 版及更新版本中的實例，您最多可以將 51 部 ESXi 伺服器新增至起始叢集，以及最多可以將 59 部 ESXi 伺服器新增至已新增的叢集。

如果是部署在 2.1 版或更早版本中的實例，您必須啟用必要的 vSAN 支援，才能將叢集大小增加到超過 32。請完成下列步驟以啟用必要的 vSAN 支援：

1. 在每一部已部署的 ESXi 伺服器上，執行下列指令：

   `esxcli system settings advanced set -o /VSAN/goto11 -i 1`

   `esxcli system settings advanced set -o /Net/TcpipHeapMax -i 1576`

2. 重新啟動每一部 ESXi 伺服器。如需相關資訊，請參閱 [Creating a vSAN 6.x cluster with up to 64 hosts](https://kb.vmware.com/s/article/2110081)。
3. 您可能需要增加 vCenter Server 的大小，以容納所新增的虛擬機器及 ESXi 伺服器。
4. 開啟「IBM 支援中心」問題單，指出您完成步驟 1 - 3 來手動套用 vSAN 變更。在問題單中，要求針對超過 32 部的 ESXi 伺服器啟用已升級實例。

## 我可以變更 ESXi 伺服器名稱及 IP 位址嗎？
{: #faq_esxi-change-name-ip}
{: faq}

無法變更 ESXi 伺服器名稱及 IP 位址，因為已登錄它們以進行 Windows DNS 解析。變更可能會導致部署期間失敗或 vCenter Server 功能失敗。

請不要在 {{site.data.keyword.cloud_notm}} 使用者介面上使用**重新命名裝置**特性來變更 ESXi 伺服器名稱。此功能會變更 ESXi 伺服器的 FQDN，但所配置的 vCenter Server 及 Windows VSI 主機登錄將不正確，而可能導致失敗。
{:note}

## 我可以在 ESXi 伺服器上停用 root 存取權嗎？
{: #faq_esxi-disable-root}
{: faq}

建議在 ESXi 伺服器上保持啟用 root 存取權，否則可能會發生 {{site.data.keyword.vmwaresolutions_short}} 功能失敗。

必要的話，當 {{site.data.keyword.vmwaresolutions_short}} 主控台上的 ESXi 伺服器狀態為**備妥使用**之後，您可以停用 root 存取權。

您必須重新啟用 root 存取權，以進行後續的自動化作業，例如，新增或移除檔案共用時，或在安裝附加服務時（例如 Zerto on {{site.data.keyword.cloud_notm}}）。

## 我可以在我的 ESXi 伺服器上新增靜態路徑，以便從其他位置裝載儲存空間嗎？
{: #faq_esxi-static-routes}
{: faq}

您可以為儲存空間新增靜態路徑，但執行時必須格外小心。否則，現有的共用可能會變成未裝載。

不支援為 vMotion 新增靜態路徑。vMotion 子網路配置中的變更可能會導致 {{site.data.keyword.vmwaresolutions_short}} 功能失敗。
{:note}

## 相關鏈結
{: #faq_esxi-related}

* [擴充及縮減 vCenter Server 實例的容量](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)
* [新增、檢視及刪除 vCenter Server 實例的叢集](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_hybrid_addingviewingclusters#vc_hybrid_addingviewingclusters)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
