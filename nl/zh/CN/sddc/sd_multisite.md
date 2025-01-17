---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-13"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation 实例的多站点配置
{: #sd_multisite}

{{site.data.keyword.vmwaresolutions_full}} 支持将实例部署在不同位置，在短时间内让这些实例启动并开始运行。

## 注释
{: #sd_multisite-notes}

* 无法在多站点配置中将 VMware Cloud Foundation 与 VMware vCenter Server 实例相链接。
* 无法将 V2.0 中部署的实例与较低发行版中的实例（即使已升级到 V2.0）相链接。

## 多站点部署组件
{: #sd_multisite-deployment-components}

多站点部署由以下组件构成。

* **主实例**：主 VMware Cloud Foundation 实例具有以下配置：
  *  Microsoft Active Directory (AD) 和 DNS（域名系统）根域
  *  Cloud Foundation 子域
  *  SSO (Single Sign-On) 域
  *  SSO 站点名称
* **辅助实例**：一个或多个辅助 Cloud Foundation 实例，这些实例与主实例相链接，配置如下：
   *  SSO 站点名称
   *  链接到主实例上根域的 DNS 子域
   *  DNS 和 AD 复制在主实例和辅助实例上的 AD 虚拟机之间设置
   *  PSC (Platform Services Controller) 部署并配置为通过主实例上的 PSC 进行复制
   *  辅助实例上的 VMware vCenter 设置为以“增强链接方式”与主实例上的 vCenter 相链接

## Cloud Foundation 多站点部署
{: #sd_multisite-deployment}

多站点配置功能使用轴辐式拓扑，其中包含一个主站点和最多七个辅助站点。支持单层站点，即无法配置链接到其他辅助站点的后续站点。在跨所有实例的多站点配置中，总共可以有 128 个 ESXi 服务器。

如果配置需要具有超过 128 个 ESXi 服务器的多站点部署，请联系 IBM 支持人员以获取帮助。有关更多信息，请参阅[联系 IBM 支持人员](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)。
{:note}

下图描绘了 Cloud Foundation 多站点部署的总体视图。

图 1. Cloud Foundation 多站点部署

![Cloud Foundation 多站点部署](../vcenter/multisite-hub-spoke.svg "Cloud Foundation 多站点部署")

该模型包含以下层：

* **主实例**：在多站点配置中，实例订购过程期间将第一个实例定义为主实例。
* **辅助实例**：在多站点配置中，订购过程期间将连接到主实例的实例定义为辅助实例。

在多站点配置中最多可以部署 8 个实例（1 个主实例和 7 个辅助实例）。

删除属于多站点配置中的 Cloud Foundation 实例需要特殊规划。有关更多信息，请参阅[删除多站点配置中的 Cloud Foundation 实例](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_deletinginstance_multi)。
{:note}

## 相关链接
{: #sd_multisite-related}

* [将主要角色分配给 NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-44E8AE16-BA3F-4DD9-B582-FC1E137E6CFC.html){:new_window}
* [配置辅助 NSX Manager](https://pubs.vmware.com/NSX-62/topic/com.vmware.nsx-cross-vcenter-install.doc/GUID-9E48BC57-15E3-49C7-8BC5-F94ED8918BBE.html){:new_window}
* [VMware vCenter Single Sign-On 支持的 Active Directory 信任](https://kb.vmware.com/kb/2064250){:new_window}
* [在 {{site.data.keyword.cloud_notm}} 中安全连接专用 VMware 工作负载](https://www.ibm.com/developerworks/library/se-securely-connect-private-vmware-workloads-ibm-cloud/index.html){:new_window}
