---

copyright:

  years:  2016, 2017

lastupdated: "2017-08-28"

subcollection: vmware-solutions


---

# V1.8 发行说明
{: #relnotes_v18}

此发行版包含新增功能、组件更新、易用性增强功能和错误修订。有关不同发行版中的已修复问题、产品已知问题以及使用 {{site.data.keyword.vmwaresolutions_full}} 的提示的列表，请参阅 [{{site.data.keyword.vmwaresolutions_short}} dW Answers](https://developer.ibm.com/answers/topics/cloudvmw/){:new_window}。

## Fortinet on IBM Cloud 服务
{: #relnotes_v18-fortinet}

Fortinet on {{site.data.keyword.cloud_notm}} 服务现在可用于 Cloud Foundation 和 vCenter Server 实例。此服务用于以高可用性方式部署 FortiGate Security Appliance (FSA) 300 系列设备对，以提供防火墙、路由、NAT 和 VPN 服务来保护实例公用 VLAN 上的所有服务器和虚拟机。您可以在订购实例时订购包含 Fortinet 服务的实例，也可以日后在实例详细信息页面中向现有实例添加此服务。

成功安装 Fortinet 服务后，可以在 FortiGate 控制台中管理和配置 FSA 的防火墙规则。必须确保将 FSA 防火墙规则定义为允许通过管理组件（例如，IBM CloudDriver 虚拟机或 Zerto Virtual Manager）启动的出站 HTTPS 通信，以便通过因特网与 IBM Bluemix® 上的外部管理数据库进行通信。出站 HTTPS 通信从实例中的管理服务 VMware NSX Edge 服务网关 (ESG) 的公共 IP 地址发起。

有关更多信息，请参阅以下主题：
* [Fortinet on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-fsa_considerations)
* [管理 Fortinet on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingfsa)

## Veeam on IBM Cloud 服务
{: #relnotes_v18-veeam}

此发行版引入了 Veeam on {{site.data.keyword.cloud_notm}} 服务，此服务可以同时备份管理组件和工作负载。此新服务将取代仅备份管理组件且集成在 V1.8 之前发行版中的先前 Veeam VSI。

由于此更改，虽然 1.8 之前的实例中的 Veeam VSI 保持运行，但实例的备份点在 {{site.data.keyword.vmwaresolutions_short}} 控制台中不再可用，您必须创建支持凭单以获取有关复原的帮助。

此外，V1.8 之前版本的实例中的 Veeam VSI 许可证已于 2017 年 10 月 14 日到期。因此，您必须尽早将先前的 Veeam VSI 替换为新的 Veeam 服务。

有关更多信息，请参阅以下主题：
* [Veeam on {{site.data.keyword.cloud_notm}} 概述](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [管理 Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)

## 对 VMware Cloud Foundation 实例的更新
{: #relnotes_v18-vcf}

### 订购 Cloud Foundation 实例时自带 VMware 许可证 (BYOL)
{: #relnotes_v18-byol}

从 V1.8 发行版开始，订购 Cloud Foundation 实例时，会向您提供两个用于许可实例的 VMware 组件（包括 vSphere、vCenter Server、NSX 和 vSAN）的选项。您可以选择使用要以您的名义购买的新许可证。

还可以选择对组件使用您自己的 VMware 许可证，这样就需要您提供许可证密钥。在此情况下，对于您提供了许可证的 VMware 组件，将由 VMware 而不是 IBM 支持人员来提供后续支持。

## 对 VMware vCenter Server 实例的更新
{: #relnotes_v18-vcs}

### 定制实例的 CPU 和内存
{: #relnotes_v18-custom-cpu}

在预构建并经过测试的“小型”、“中型”和“大型”选项旁边，提供了可定制服务器选项。除了 RAM 量之外，还可以根据双 CPU 以及总核心数，从 VMware HCL 兼容服务器列表中进行选择。本地存储器不可定制。

有关更多信息，请参阅以下主题：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

### 支持添加 7 个以上的 NFS 文件共享
{: #relnotes_v18-nfs}

 在集群中的所有 ESXi 服务器上，最多可以连接 32 个文件共享。

 有关更多信息，请参阅以下主题：
* [订购 vCenter Server 实例](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_orderinginstance)
* [添加、查看和删除 vCenter Server 实例的集群](/docs/services/vmwaresolutions?topic=vmware-solutions-vc_addingviewingclusters#vc_addingviewingclusters)

### 对数据中心的更新
{: #relnotes_v18-dc}

以下新数据中心可用于部署：**DAL-09、DAL-12 和 DAL-13 - 达拉斯**；**LON-04 和 LON-06 - 伦敦**；**SJC-04 - 圣何塞**；**WDC-06 和 WDC-07 - 华盛顿**

有关更多信息，请参阅[针对 vCenter Server 实例的需求和规划](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)

## 易用性增强功能
{: #relnotes_v18-ui}

对整个用户界面进行了改进：
* 可以在左侧导航窗格中的**开始**页面上，了解有关服务的信息并订购实例。
* 使用实例详细信息页面上的溢出菜单来删除处于**可供使用**状态的实例。
* 现在**更新和补丁**选项卡上提供了用于升级 NSX 许可证版本的选项。许可证升级会将 IBM SoftLayer 帐户中的所有现有 NSX 许可证替换为新许可证。
* 实例详细信息页面上的**备份和复原**选项卡不再可用。
* 可以在订购一开始，就选择多个要部署的服务。除了 Zerto on {{site.data.keyword.cloud_notm}} 服务外，还提供了用于选择 Veeam on {{site.data.keyword.cloud_notm}} 服务和 Fortinet on {{site.data.keyword.cloud_notm}} 服务的选项。
* 实例详细信息页面中**服务**选项卡上的**可用服务**选项卡已重命名为**添加服务**。
