---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Ordering and configuring IBM Cloud Object Storage with Veeam
{: #icos_ordering}

With the release of Veeam Availability Suite 9.5 Update 4, Veeam is compatible with IBM Cloud Object Storage (ICOS). The ordering of IBM Cloud Object Storage is not automated when ordering Veeam on IBM Cloud, but it can be added after deployment.

To order IBM Cloud Object Storage, complete the following tasks in the specified order.

## Creating an Object Storage instance
{: #icos_ordering-obj}

To create an Object Storage instance, see [Creating a new service instance](/docs/services/cloud-object-storage/basics?topic=cloud-object-storage-provision#provision-instance). Follow the steps and return to this section to continue with the following tasks.

## Creating a bucket
{: #icos_ordering-bucket}

To create a bucket, see [Create some buckets to store your data](/docs/services/cloud-object-storage?topic=cloud-object-storage-getting-started#gs-create-buckets). Follow the steps and return to this section to continue with the following tasks.

## Creating service credentials
{: #icos_ordering-service-cred}

To create service credentials, including HMAC credentials, see [Service credentials](/docs/services/cloud-object-storage/hmac?topic=cloud-object-storage-service-credentials#using-hmac-credentials). Follow the steps and return to this section to continue with the following tasks.

## Adding a scale-out repository
{: #icos_ordering-scale-repo}

To add a scale-out repository within Veeam, see [Adding scale-Out repositories](https://helpcenter.veeam.com/docs/backup/vsphere/sobr_add.html?ver=95u4){:new_window}. Follow the steps and return to this section to continue with the following tasks.

## Maintaining and managing your cloud tier
{: #icos_ordering-manage-cloud}

For information about maintaining and managing your cloud tier, see [Managing capacity tier data](https://helpcenter.veeam.com/docs/backup/vsphere/capacity_tier_managing_data.html?ver=95u4){:new_window}.

## Related links
{: #icos_ordering-related}

* [Veeam on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions?topic=vmware-solutions-veeam_considerations)
* [Ordering Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_ordering)
* [Managing Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managingveeam)
* [Requesting managed services for Veeam on {{site.data.keyword.cloud_notm}}](/docs/services/vmwaresolutions/services?topic=vmware-solutions-managing_veeam_services)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
