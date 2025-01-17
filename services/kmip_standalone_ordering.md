---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-08"

subcollection: vmware-solutions


---

# Ordering KMIP for VMware on IBM Cloud instances
{: #kmip_standalone_ordering}

You can order a KMIP for VMware on {{site.data.keyword.cloud}} instance without associating it to any VMware instance for flexible management of the service and instances.

## Before you begin
{: #kmip_standalone_ordering-req}

Ensure that you completed the following tasks:
* You configured the {{site.data.keyword.cloud_notm}} infrastructure credentials on the **Settings** page. For more information, see [User accounts and settings](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-useraccount).
* You reviewed all the considerations in [Considerations when installing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions?topic=vmware-solutions-kmip_standalone_considerations#kmip_standalone_considerations-install).

## Procedure to order KMIP for VMware on IBM Cloud instances
{: #kmip_standalone_ordering-procedure}

1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Getting started** from the left navigation pane.
2. In the **Order additional services** area, click **KMIP for VMware on IBM Cloud**.
3. On the **KMIP for VMware on IBM Cloud** page, configure the service settings as required.
4. Click **Provision**.

## KMIP for VMware on IBM Cloud service configuration
{: #kmip_standalone_ordering-config}

When you order this service, provide the following settings:

### Instance Name
{: #kmip_standalone_ordering-config-instance-name}

Specify a name for your KMIP for VMware on {{site.data.keyword.cloud_notm}} instance.

### Service Location
{: #kmip_standalone_ordering-config-service-region}

Select the {{site.data.keyword.cloud_notm}} location where your KMIP for VMware on {{site.data.keyword.cloud_notm}} instance is to be hosted.

{{site.data.keyword.cloud_notm}} maintains a highly available KMIP for VMware on {{site.data.keyword.cloud_notm}} network service endpoint in each location where the service is available.

Table 1. KMIP for VMware on {{site.data.keyword.cloud_notm}} network service endpoint locations

| Location         | Endpoints               |
|:---------------|:-----------------------|
| Dallas | <ul><li><code>kmip-1.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Frankfurt |  <ul><li><code>kmip-1.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.eu-central.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| London | <ul><li><code>kmip-1.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.uk-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Sydney |  <ul><li><code>kmip-1.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-south.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Tokyo | <ul><li><code>kmip-1.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.ap-north.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |
| Washington DC | <ul><li><code>kmip-1.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li><li><code>kmip-2.private.us-east.vmware-solutions.cloud.ibm.com:5696</code></li></ul> |

### API Key for Service ID
{: #kmip_standalone_ordering-config-api-key}

Enter the API key for the {{site.data.keyword.cloud_notm}} Service ID that is used to access the service instance of Key Protect or Hyper Protect Crypto Services.

### Key Manager Instance
{: #kmip_standalone_ordering-config-key-protect}

Click **Retrieve** to get the list of available key manager instances and select the one to use for key management.

### Customer Root Key
{: #kmip_standalone_ordering-config-root-key}

Click **Retrieve** to get the customer root key that is stored in your selected key manager instance.

## Results
{: #kmip_standalone_ordering-results}

The ordering of the KMIP for VMware on {{site.data.keyword.cloud_notm}} instance starts automatically. You receive confirmation that the order is being processed and you can check the status of the order by viewing the instance details.

When the instance is ready to use, the status of the instance is changed to **Installed** and you receive a notification by email.

## What to do next
{: #kmip_standalone_ordering-next}

Add client certificates for the KMIP for VMware on {{site.data.keyword.cloud_notm}} instance that you ordered. For more information, see [Adding, viewing, and deleting certificates for KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_addingdeletingcert).

## Related links
{: #kmip_standalone_ordering-related}

* [Viewing KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_viewing)
* [Deleting KMIP for VMware on {{site.data.keyword.cloud_notm}} instances](/docs/services/vmwaresolutions/services?topic=vmware-solutions-kmip_standalone_deleting)
* [Activity Tracker events](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-at-events)
