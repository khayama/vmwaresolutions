---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-13"

subcollection: vmware-solutions


---

# IBM Cloud アカウントへの V2.5 より前の vCenter Server インスタンスのマイグレーション
{: #vc_addinstancetousraccount}

V2.5 以降のリリースで {{site.data.keyword.cloud}} アカウントにデプロイされた VMware vCenter Server インスタンスは、自動的にアカウントに追加されて、{{site.data.keyword.cloud_notm}} Identity and Access Management (IAM) によって管理されます。

V2.4 以前のリリースでデプロイされたインスタンスの場合、それらを IAM 対応のユーザー管理のために指定の {{site.data.keyword.cloud_notm}} アカウントにマイグレーションできます。

## 始める前に
{: #vc_addinstancetousraccount-prereq}

インスタンスのマイグレーション先となる {{site.data.keyword.cloud_notm}} アカウントが IaaS 専用アカウントでないことを確認します。 IaaS 専用アカウントは、{{site.data.keyword.cloud_notm}} アカウントにリンクされていない {{site.data.keyword.cloud_notm}} インフラストラクチャー・アカウントです。

IaaS 専用アカウントと PaaS アカウントをリンクする方法について詳しくは、[Follow these steps to link your IaaS and PaaS accounts](https://www.ibm.com/cloud/blog/follow-steps-link-iaas-paas-accounts){:new_window} を参照してください。

## インスタンスをマイグレーションする手順
{: #vc_addinstancetousraccount-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. コンソール・バナーのユーザー・アカウント・アイコンをクリックし、**「アカウント」**フィールドをクリックして、インスタンスのマイグレーション先となるユーザー・アカウントを選択します。
3. **「vCenter Server インスタンス」**の表で、V2.5 より前のインスタンスを見つけます。
4. **「アクション」**列でオーバーフロー・メニュー・アイコンをクリックし、**「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**をクリックします。
5. **「アカウントへのインスタンスのマイグレーション (Migrate Instance to Account)」**ウィンドウで、インスタンスのマイグレーション先のアカウントを確認してから**「マイグレーション」**をクリックします。

### 結果
{: #vc_addinstancetousraccount-results}

1. 指定された {{site.data.keyword.cloud_notm}} アカウントへのインスタンスのマイグレーション要求が受け入れられたことを示すコンソール通知が表示されます。
2. インスタンスのマイグレーションが完了すると、マイグレーション先のアカウントの下の**「リソース」**ページにインスタンスが表示されます。 マイグレーション済みのインスタンスは、マイグレーション元のアカウントには表示されなくなります。

## 関連リンク
{: #vc_addinstancetousraccount-related}

* [IAM でのユーザー・アクセス権限の管理](/docs/services/vmwaresolutions/services?topic=vmware-solutions-iam#iam)
* [サービスとリソースにアクセスするようにユーザーを招待する](/docs/services/vmwaresolutions/vmonic?topic=vmware-solutions-iamuserinvite)
* [IBM Cloud IAM とは](/docs/iam?topic=iam-iamoverview)
