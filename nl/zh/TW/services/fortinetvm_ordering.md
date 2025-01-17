---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-09"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# 訂購 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering}

您可以在訂購包含服務的新實例時，同時訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud}} 服務，或將服務新增至現有實例。

## 為新實例訂購 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-new}

您可以使用下列其中一種方法，訂購包含 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的新實例：
* 當您從 {{site.data.keyword.vmwaresolutions_short}} 主控台訂購新實例時，請選取**服務**區段中的 **FortiGate Virtual Appliance on IBM Cloud**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **FortiGate Virtual Appliance on IBM Cloud**，指定服務設定，然後選取**新增至新實例**。

## 為現有實例訂購 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-existing}

您可以使用下列其中一種方法，將 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 服務新增至現有實例：
* 從 {{site.data.keyword.vmwaresolutions_short}} 主控台，檢視您要為其新增服務的實例，按一下左導覽窗格上的**服務**，然後按一下**新增**。
* 從 {{site.data.keyword.cloud_notm}} 型錄中，選取 **FortiGate Virtual Appliance on IBM Cloud**，指定服務設定，然後選取**新增至現有實例**。

## 為專用實例訂購 FortiGate Virtual Appliance on IBM Cloud
{: #fortinetvm_ordering-private}

為未配置公用介面的實例訂購 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 時，必須提供 Proxy 伺服器以完成安裝。HTTP Proxy 伺服器必須已配置並透過虛擬遞送及轉遞 (VRF) 提供，才能開始安裝 Fortigate Virtual Appliance on {{site.data.keyword.cloud_notm}}。

為了確保持續運行，FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 必須可透過網際網路持續存取 Fortigate 授權伺服器。

## FortiGate Virtual Appliance on IBM Cloud 服務配置
{: #fortinetvm_ordering-config}

當您訂購此服務時，請提供下列設定。

### FortiGuard 網路連線
{: #fortinetvm_ordering-config-network-connect}

為 FortiGuard 選取**公用網路**或**專用網路**。如果目標叢集配置了僅限專用網路介面，則只能使用**專用網路**選項。此選項可決定 FortiGuard 如何聯絡 Fortinet 授權伺服器來啟動授權及下載安全修補程式，這不會影響工作負載資料平面。

如果您選取**專用網路**，請指定下列設定：
* **Proxy IP 位址**：Proxy 伺服器的 IPv4 位址。
* **Proxy 埠號**：Proxy 伺服器的埠號，通常是 8080 或 3128。
* **Proxy 使用者名稱**：如果您需要 Proxy 鑑別，請輸入 Proxy 伺服器的使用者名稱。
* **Proxy 密碼**：如果您需要 Proxy 鑑別，請輸入 Proxy 伺服器的密碼。

### 名稱 
{: #fortinetvm_ordering-config-name}

輸入服務名稱。

### 部署大小
{: #fortinetvm_ordering-config-size}

{{site.data.keyword.cloud_notm}} 提供下列部署大小選項：
* 小型（2 個 vCPU/4 GB RAM）
* 中型（4 個 vCPU/6 GB RAM）
* 大型（8 個 vCPU/12 GB RAM）

### 授權模型
{: #fortinetvm_ordering-config-license}

FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 的授權模型提供下列選項：
<dl class="dl">
        <dt class="dt dlterm">Standard FW</dt>
        <dd class="dd">此組合包含「有狀態封包檢驗」、「VLAN 保護及進階記載」、「Ingress 及 Egress 防火牆規則」、「SSL/IPSec VPN 終止」，以及 24 小時全年無休的支援。</dd>
        <dt class="dt dlterm">Standard FW + UTM</dt>
        <dd class="dd">除了「進階惡意軟體保護 (AMP)」服務之外，此組合還包括所有標準防火牆服務。它包括防毒、Botnet IP/網域服務、行動惡意軟體安全、FortiSandbox Cloud、Virus Outbreak Protection Service 和 Content Disarm & Reconstruct。它也包括 Web 過濾、IPS、反垃圾郵件、應用程式控制項和 FortiCare 服務。</dd>
        <dt class="dt dlterm">Standard FW + Enterprise</dt>
        <dd class="dd">除了下列服務之外，此組合還包括所有標準防火牆和 UTM 服務：<ul><li>雲端存取安全分配管理系統 (CASB) - 此服務為雲端型服務提供可見性、相符性、資料安全及威脅保護。</li><li>工業安全 - 此服務為一般 ICS/SCADA 通訊協定提供簽章。</li><li>安全評級 - 此服務提供審核功能，以識別重要漏洞和配置弱點，並實作最佳作法建議。</li></ul></dd>
</dl>

在 2018 年第三季，Fortinet 在其企業組合中新增了三項新服務（CASB、「工業安全」和「安全評級」）。這些服務僅適用於 FortiGate 6.0。
{:note}

您無法在安裝服務之後變更授權模型。若要變更授權模型，您必須移除現有服務，然後選取不同的授權選項來重新安裝服務。
{:important}

## 相關鏈結
{: #fortinetvm_ordering-related}

* [FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}} 概觀](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fortinetvm_considerations)
* [管理 FortiGate Virtual Appliance on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfortinetvm)
* [訂購、檢視及移除 vCenter Server 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices)
* [訂購、檢視及移除 vCenter Server with Hybridity Bundle 實例的服務](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_hybrid_addingremovingservices)
* [與 IBM 支援中心聯絡](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [常見問題](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Fortinet 網站](https://www.fortinet.com/){:new_window}
* [Fortinet 文件庫](https://docs.fortinet.com/product/fortigate/6.2){:new_window}
