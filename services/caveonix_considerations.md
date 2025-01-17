---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-12"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Caveonix RiskForesight on IBM Cloud overview
{: #caveonix_considerations}

The Caveonix RiskForesight on {{site.data.keyword.cloud}} service can help to manage cyber and compliance risk with proactive monitoring and automated defense controls to protect against threats and to meet industry or government regulations.

This service is available only to VMware vCenter Server on {{site.data.keyword.cloud_notm}} instances that are deployed in V2.9 and later releases.
{:note}

## Technical specifications for Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-specs}

The following components are ordered and included in the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service.

### vCenter resources
{: #caveonix_considerations-tech-specs-vcenter}

* CPU: 8 vCPU
* RAM: 32 GB
* Disk: 80 GB

### Network
{: #caveonix_considerations-tech-specs-network}

A dedicated private subnet with 64 IP addresses is ordered.

### Licenses and fees
{: #caveonix_considerations-tech-specs-license-fee}

A Caveonix RiskForesight license key is ordered for each instance of the service.

## Considerations when you install Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-install}

Before you install the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service, ensure that the CPU and memory in the default cluster of your service instance is sufficient for the Caveonix RiskForesight virtual machine.

## Considerations when you remove Caveonix RiskForesight on IBM Cloud
{: #caveonix_considerations-remove}

Review the following considerations before you remove the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service:
* Removing the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service does not cancel the Caveonix RiskForesight license. You must delete the Caveonix RiskForesight license from the **Caveonix RiskForesight Licenses** table on the **Resources** page in the {{site.data.keyword.vmwaresolutions_short}} console.
* When you remove the service, the {{site.data.keyword.vmwaresolutions_short}} automation deletes only the single "all-in-one" Caveonix VM that was deployed and the dedicated private subnet that was ordered for it. Therefore,
   * If you scaled out the Caveonix VM into multiple VMs, those additional VMs are not removed.
   * If you used the IP addresses of the dedicated private subnet on additional VMs, those VMs must be assigned new IP addresses to continue to function.
   * If you delete vCenter Server instance A with the Caveonix RiskForesight on {{site.data.keyword.cloud_notm}} service installed, and you used the IP addresses of the dedicated private subnet ordered for the service in vCenter Server instance B, the dedicated private subnet is canceled upon deletion of vCenter Server instance A.

## Related links
{: #caveonix_considerations-related}

* [Ordering Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-caveonix_ordering)
* [Managing Caveonix RiskForesight on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingcaveonix)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
