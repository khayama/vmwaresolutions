---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# 虚拟机 vSAN 冗余
{: #vum-vsan-redundancy}

在 vSAN 集群上将 vSphere ESXi 主机置于维护模式时，需要选择数据转移方式。选择的方式可能会影响正在使用 vSAN 数据存储的虚拟机 (VM) 和设备：
* **完全数据迁移**将转移主机中的所有数据，并将其移至 vSAN 集群中的其他 vSphere ESXi 主机。这种转移方式会生成最大的数据传输量，并且耗用的时间和资源最多。所选主机的本地存储器上的所有组件都会迁移到集群中的其他位置。主机进入维护模式时，所有 VM 和设备都可以访问其存储组件，并且仍然符合其所分配的存储策略。完全数据转移可能需要很长时间，并且可能会使升级的维护时段持续很长时间。
* **确保可访问性数据转移**模式是缺省选项，当 vSphere ESXi 主机置于维护模式时，vSAN 可确保主机上所有可访问的 VM 或设备保持可访问。仅执行部分数据转移时，VM 或设备可能在转移期间不再完全符合 VM 存储策略，因此可能无权访问自己的所有副本。如果在主机处于维护模式时发生故障，并且主容错级别设置为 1，那么会发生数据丢失，并且 VM 或设备可能不可用。
* 在**无数据迁移**方式下，vSAN 不会在进入维护模式时，从主机中转移任何数据。虽然这可减少进入维护模式的时间，从而减少维护时段的持续时间，但某些 VM 或设备可能会变得不可访问。

此部分将创建一个新的 VM 存储策略，该策略允许选择**确保可访问性数据转移**方式以缩短维护时段，还可降低一个主机处于维护模式时另一个主机发生故障而导致 VM 或设备不可访问的风险。在将 vSAN 主机置于维护模式时，如果任何 VM 或设备变为非冗余是不可接受的，请在完成任何修复操作之前，先完成以下过程。这将需要一个至少包含 6 个主机的集群。

1. 创建具有 RAID 5/6 和 FTT =2 (RAID 6) 设置的新 vSAN 概要文件，然后针对必需的 VM 或设备应用此策略。

2. 等待 vSAN 完成同步后，再启动任何修复操作。可以通过导航至集群的 **vSAN 虚拟对象监视页面**并查看**完成状态**来检查完成状态。

## 相关链接
{: #vum-vsan-redundancy-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解决方案体系结构](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 数字技术互动](https://ibm-dte.mybluemix.net/vmware)（演示）
