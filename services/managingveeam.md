---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-28"

subcollection: vmware-solutions


---

# Managing Veeam on IBM Cloud
{: #managingveeam}

After the service is deployed into your instance, you can access the Veeam console by using RDP to manage the backup and restore of all the virtual machines in your environment, including the backup and restore of the management components. You can also upgrade the service by downloading and installing the Veeam updates from the Veeam website.

For instances that were deployed in releases earlier than V1.8, if you want to use the Veeam on {{site.data.keyword.cloud}} service, you must replace the existing Veeam VSI in the instances. For more information, see the _Replacing the Veeam VSI of pre-V1.8 instances with Veeam on IBM Cloud_ section.

## Accessing the Veeam console by using RDP
{: #managingveeam-accessing}

To manage the Veeam on {{site.data.keyword.cloud_notm}} service, access the Veeam console by completing the following steps:
1. Use Remote Desktop Protocol (RDP) to connect to the Windows IP address.
2. Log in to the Windows console by using the Administrator credentials.
3. Access the Veeam console from the Windows console by using the Administrator credentials.

You can find the Windows IP address and the Administrator credentials on the Veeam on {{site.data.keyword.cloud_notm}} service details page.

For more information, see [Ordering, viewing, and removing services for vCenter Server instances](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservices).

## Backing up and restoring management components for instances that have Veeam on IBM Cloud installed
{: #managing-veeam-backup-and-replication}

The Veeam on {{site.data.keyword.cloud_notm}} service can be configured to back up the management components by using the Veeam console. For more information, see [Backing up components](/docs/services/vmwaresolutions/archiref/solution?topic=vmware-solutions-solution_backingup).

For instances deployed in (or upgraded to) V1.8 or later releases, the configuration changes to your environment are not automatically backed up. Therefore, before you change the configuration of your environment, it is recommended that you back up the management components manually by running the management backup job in the Veeam console. For more information about backing up manually, see the [Veeam technical instructions](https://helpcenter.veeam.com/backup/vsphere/scheduing_manual.html){:new_window}.

When failures occur on the management components, you can restore the management components to a previous backup by using the Veeam console. For more information about restoring manually, see the [Veeam technical instructions]( https://helpcenter.veeam.com/backup/vsphere/performing_full_recovery.html){:new_window}.

## Applying updates to Veeam on IBM Cloud
{: #managingveeam-updates}

You are responsible for maintaining the Veeam software to keep it updated to the most recent version.

### Applying updates for instances deployed with public and private network
{: #managingveeam-updates-public-private}

If the Veeam service is installed on an instance with public and private network, you can check for and download the updates by using the Veeam software itself.

### Applying updates for instances deployed with private network only
{: #managingveeam-updates-private}

If the Veeam service is installed on an instance with private network only, because the Veeam VSI is configured with no public network access, you cannot check for or download updates by using the Veeam software itself. Instead, you must download updates from the Veeam website, transfer them to the Veeam VM, and then install them.

## Updating Veeam licenses
{: #managingveeam-update-license}

### Updating Veeam licenses for instances deployed with public and private network
{: #managingveeam-update-license-public-private}

If the Veeam service is installed on an instance with public and private network, you can update your Veeam license either automatically or manually by following the Veeam instructions at [Updating license]( https://helpcenter.veeam.com/docs/backup/vsphere/license_update.html).

### Updating Veeam licenses for instances deployed with private network only
{: #managingveeam-update-license-private}

If the Veeam service is installed on an instance with private network only, you must take note of the expiration date for your license and [contact IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support) to get assistance with updating the license key when the renewal is needed.

## Replacing the Veeam VSI of pre-V1.8 instances with Veeam on IBM Cloud
{: #managingveeam-replace-vsi}

The Veeam on {{site.data.keyword.cloud_notm}} service, which can back up both management components and workloads, supersedes the previous Veeam VSI that was integrated into VMware vCenter Server in releases earlier than V1.8 for the backup of management components only.

Because of this change, the previous **Backup and Restore** tab on the instance details page was removed and the backup points for the instances are no longer available in the {{site.data.keyword.vmwaresolutions_short}} console, although the Veeam VSI in the pre-V1.8 instances keeps working.

You must create an {{site.data.keyword.cloud_notm}} Support ticket to get assistance with a restore. In addition, the license of the Veeam VSI in pre-V1.8 instances expired on 14 October 2017. Therefore, you must replace the previous Veeam VSI with the new Veeam on {{site.data.keyword.cloud_notm}} service.

Complete the following steps:
1. In the {{site.data.keyword.vmwaresolutions_short}} console, click **Resources** from the left navigation pane, and then click the target instance.
2. On the instance details page, click the **Update and Patch** tab. Ensure that you upgraded the instance to the V1.8 release.
3. Click the **Services** tab.
4. On the **Add Services** tab, install the Veeam on {{site.data.keyword.cloud_notm}} service.

After the new Veeam on {{site.data.keyword.cloud_notm}} service is deployed and a successful backup of your management components is completed, you can remove the existing Veeam VSI from your account by creating an {{site.data.keyword.cloud_notm}} Support ticket. IBM Support identifies and deletes the existing Veeam VSI and storage.

## Related links
{: #managingveeam-related}

* [Veeam on {{site.data.keyword.cloud_notm}} overview](/docs/services/vmwaresolutions/services?topic=vmware-solutions-veeam_considerations)
* [Contacting IBM Support](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-trbl_support)
* [FAQ](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-faq)
* [Veeam.com website](https://www.veeam.com/)
* [Veeam technical documentation](https://www.veeam.com/documentation-guides-datasheets.html)
