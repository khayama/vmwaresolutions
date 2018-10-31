---

copyright:

  years:  2016, 2018

lastupdated: "2018-10-03"

---

# 扫描和复查

扫描主机、虚拟机和虚拟设备时，您可根据基线和基线组对其进行评估，以确定其一致性级别。这将扫描库存对象，并复查结果以确定它们与基线和基线组的一致程度。可以通过文本搜索、组选择、基线选择和一致性状态选择来过滤扫描结果。您可以启动以下扫描：
*	**手动启动 vSphere ESXi 主机扫描** - 可以根据连接的基线和基线组来扫描 vSphere 库存中的 vSphere ESXi 主机。
*	**手动启动虚拟机和虚拟设备扫描** - 可以根据连接的基线和基线组来扫描 vSphere 库存中的虚拟机和虚拟设备。
*	**手动启动容器对象扫描** - 通过扫描作为数据中心或数据中心文件夹的容器对象，对主机、虚拟机和虚拟设备启动同时扫描。
*	**安排扫描** - 可以配置 vSphere Web Client 以在特定时间扫描虚拟机、虚拟设备和 ESXi 主机，或按您方便的时间间隔对这些对象进行扫描。

##	手动启动 vSphere ESXi 主机扫描

1.	单击**扫描更新**按钮，选择**补丁、扩展和升级**，然后单击**确定**。
2.	扫描完成后，选择**关键主机补丁**，然后在下方窗格中，针对每个主机进行复查。
3.	通过单击“补丁数”中的数字，将有一个窗口会显示补丁详细信息。
4.	查看**非关键补丁**，并重复上述步骤。

请注意，VUM 日志文件可能位于 _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

##	手动启动虚拟机和虚拟设备扫描

可以根据连接的基线和基线组来扫描 vSphere 库存中的虚拟机和虚拟设备。这将根据连接的基线扫描所选虚拟机和设备，具体取决于您选择的选项。此外，还会扫描所有子对象，因此虚拟基础架构越大，在其中启动扫描的对象层次结构中的层级越高，扫描用时就越长，一致性视图也越准确。

1.	使用 vSphere Web Client，选择**主页** > **VM 和模板**。
2.	右键单击_虚拟机_ > _虚拟设备_或_虚拟机和虚拟设备的文件夹_，然后单击**扫描更新**。
3.	选择要扫描以查找的更新的类型。选项包括_虚拟设备升级、VM 硬件升级_和 _VMware Tools 升级_。
4.	单击**扫描**。

##	手动启动容器对象扫描

通过扫描作为数据中心或数据中心文件夹的容器对象，对主机、虚拟机和虚拟设备启动同时扫描。
1.	使用 vSphere Web Client，选择**主页** > **VM 和模板**。
2.	右键单击_数据中心_或_数据中心文件夹_，并单击**扫描更新**。
3.	选择要扫描以查找的更新的类型。选项包括_虚拟设备升级、VM 硬件升级_和 _VMware Tools 升级_。
4.	单击**扫描**。

##	安排扫描

可以配置 vSphere Web Client 以在特定时间扫描虚拟机、虚拟设备和 vSphere ESXi 主机，或按您方便的时间间隔对这些对象进行扫描。

1.	使用 vSphere Web Client 从库存中选择对象。系统还会扫描您选择的对象的所有子对象。
2.	选择**监视器**选项卡，然后单击**任务和事件**。
3.	选择**安排的任务**，然后单击**安排新任务**。
4.	从显示的下拉列表中，选择**扫描更新**。这将打开“扫描更新”向导。
5.	在“编辑设置”页面上，选择要扫描库存对象以查找其更新的类型。必须至少选择一种扫描类型。在“安排选项”页面上，描述扫描任务并对其进行安排。
6.	输入扫描任务的唯一名称和（可选）描述。单击**更改**以设置扫描任务的频率和开始时间。单击**确定**。
7.	扫描任务会在 vSphere Web Client 的“安排的任务”视图中列出。

### 相关链接

* [VMware HCX on IBM Cloud 解决方案](https://www.ibm.com/cloud/garage/files/HCX_Architecture_Design.pdf)
* [VMware Solutions on IBM Cloud 数字技术互动](https://ibm-dte.mybluemix.net/ibm-vmware)（演示）