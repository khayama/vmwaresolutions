---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# 完全分布式
{: #caveonix-fully}

根据资产数和数据保留需求，添加了其他基本虚拟机 (VM) 和横向扩展 VM。

表 1. 基本 - 用户界面

|参数|值|
|---|---|
|类型|基本|
|VM 数量|2|
|vCPU|2|
|RAM|6 GB|
|磁盘|60 GB|
|操作系统|CentOS 7|
|已安装的应用程序组件|UI|

表 2. 基本 - 应用程序和插件

|参数|值|
|---|---|
|类型|基本|
|VM 数量|2|
|vCPU|8|
|RAM|16 GB|
|磁盘|500 GB|
|操作系统|CentOS 7|
|已安装的应用程序组件|应用程序，插件|

表 3. 基本 - 中央收集器

|参数|值|
|---|---|
|类型|基本|
|VM 数量|3|
|vCPU|8|
|RAM|16 GB|
|磁盘|500 GB|
|操作系统|CentOS 7|
|已安装的应用程序组件|中央收集器（集群）|

表 4. 基本 - 关系数据库

|参数|值|
|---|---|
|类型|基本|
|VM 数量|2|
|vCPU|8|
|RAM|16 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|关系数据存储（主/辅助）|

表 5. 基本 - 消息传递数据存储

|参数|值|
|---|---|
|类型|基本|
|VM 数量|3|
|vCPU|8|
|RAM|16 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|消息传递数据存储（集群）|

表 6. 基本 - 索引数据存储（主节点）

|参数|值|
|---|---|
|类型|基本|
|VM 数量|3|
|vCPU|8|
|RAM|16 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|索引数据存储（主节点）|

表 7. 数据库 - 索引数据存储（数据节点）

|参数|值|
|---|---|
|类型|基本|
|VM 数量| 5 |
|vCPU|8|
|RAM|16 GB|
|磁盘|4 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|索引数据存储（数据节点）|

下表中描述了横向扩展 VM 详细信息。

表 8. 横向扩展 - 数据节点

|参数|值|
|---|---|
|类型|横向扩展|
|VM 数量	28|
|vCPU|8|
|RAM|16 GB|
|磁盘|4 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|数据节点（横向扩展）|

下表中显示了远程收集器 VM 详细信息。

表 9. 远程收集器

|参数|值|
|---|---|
|VM 数量|根据需要|
|vCPU|8|
|RAM|8 GB|
|磁盘|1 TB|
|操作系统|CentOS 7|
|已安装的应用程序组件|远程收集器|

## 相关链接
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
