---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-03"

subcollection: vmware-solutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# vCenter Server with NSX-T インスタンスの容量の拡張と縮小
{: #vc_nsx-t_addingremovingservers}

VMware vCenter Server with NSX-T インスタンスの容量は、ESXi サーバーまたはネットワーク・ファイル・システム (NFS) ストレージを追加/削除することで、ビジネス・ニーズに応じて拡張/縮小できます。

* V3.0 リリース以降、**「使用可能」**状態にある複数のクラスターで、NFS ストレージと ESXi サーバーを同時に追加/削除できるようになりました。 例えば、あるクラスターで ESXi サーバーを追加または削除したり、別のクラスターで NFS ストレージを追加または削除したりできます。
* V2.9 リリース以降では、サーバーが保守モードの間に、新規 ESXi サーバーをクラスターに追加できます。 また、複数のクラスター間で同時に ESXi サーバーを追加/削除できます。

**注**:
* 初期クラスターのストレージが vSAN の場合、デプロイメント後に 1 つ以上の ESXi サーバーを追加すると、クラスター・ストレージの容量を増やすことができます。
* 既存の NFS クラスターまたは vSAN vCenter Server with NSX-T クラスターの NFS ストレージ共有を追加/削除することができます。

## vCenter Server with NSX-T インスタンスへの ESXi サーバーの追加
{: #vc_nsx-t_addingremovingservers-adding}

### ESXi サーバーを追加する前に
{: #vc_nsx-t_addingremovingservers-adding-prereq}

* 可能な限り、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを追加してください。VMware vSphere Web Client で行った変更は {{site.data.keyword.vmwaresolutions_short}} コンソールと同期しないためです。 したがって、オンプレミス ESXi サーバーの場合、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できないまたは管理するつもりがない ESXi サーバーの場合のみ、vCenter Server に ESXi サーバーを追加してください。
* NFS ストレージのある vCenter Server with NSX-T インスタンスには、少なくとも 3 つの ESXi サーバーが必要です。 デフォルトのクラスターを拡張して、最大 51 台の ESXi サーバーを含められます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。
* vSAN ストレージのある vCenter Server with NSX-T インスタンスには、少なくとも 4 つの ESXi サーバーが必要です。

### ESXi サーバーを追加する手順
{: #vc_nsx-t_addingremovingservers-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を入力します。
7. オプションで、保守モード中にサーバーを追加するためのチェック・ボックスを選択します。
8. 見積もりコストを確認し、**「追加」**をクリックします。

### ESXi サーバーを追加した結果
{: #vc_nsx-t_addingremovingservers-adding-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

保守モード時に ESXi サーバーを追加する場合、クラスターの保守モードを解除するまで仮想マシン (VM) は新規サーバーにマイグレーションされません。   
{:important}

## vCenter Server with NSX-T インスタンスからの ESXi サーバーの削除
{: #vc_nsx-t_addingremovingservers-removing}

### ESXi サーバーを削除する前に
{: #vc_nsx-t_addingremovingservers-removing-prereq}

* 可能な限り、{{site.data.keyword.vmwaresolutions_full}} コンソールを使用して ESXi サーバーを削除してください。vSphere Web Client で行った変更は {{site.data.keyword.vmwaresolutions_short}} コンソールと同期しないためです。 したがって、オンプレミス ESXi サーバーの場合、または {{site.data.keyword.vmwaresolutions_short}} コンソールで管理できないまたは管理するつもりがない ESXi サーバーの場合のみ、vCenter Server から ESXi サーバーを削除してください。
* NFS ストレージを使用する vCenter Server with NSX-T インスタンスには少なくとも 3 つの ESXi サーバーが必要であり、vSAN ストレージを使用する vCenter Server with NSX-T インスタンスには少なくとも 4 つの ESXi サーバーが必要です。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての VM は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して ESXi サーバーを削除します。

### ESXi サーバーを削除する手順
{: #vc_nsx-t_addingremovingservers-removing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを削除するクラスターをクリックします。
5. **「ESXi サーバー」**セクションで、削除するサーバーを選択し、**「削除」**をクリックします。

### ESXi サーバーを削除した結果
{: #vc_nsx-t_addingremovingservers-removing-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されます。

   削除した ESXi サーバーについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

## vCenter Server with NSX-T インスタンスへの NFS ストレージの追加
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-to-vcs-nsx-t}

### NFS ストレージを追加する前に
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-prereq}

VMware vSphere Web クライアントから NFS ストレージの追加を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。 IBM は、お客様がインスタンスに手動で追加した NFS ファイル共有を管理しません。

### NFS ストレージを追加する手順
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、NFS ストレージを追加するクラスターをクリックします。
5. **「ストレージ」**セクションで**「追加」**をクリックします。
6. **「ストレージ」**ウィンドウで、ストレージ構成を入力します。
   * 追加するすべてのファイル共有に同じ設定を構成する場合は、**「共有の数」**、**「パフォーマンス」**、**「サイズ (GB)」**を指定します。
   * ファイル共有を個々に追加して構成する場合は、**「共有を個別に構成」**を選択し、ファイル共有ごとに、** 「共有ストレージの追加」**ラベルの横にある**「+」**アイコンをクリックして、**「パフォーマンス」**と**「サイズ (GB)」**を選択します。 少なくとも 1 つのファイル共有を選択する必要があります。
7. **「NFS ストレージの追加」**をクリックします。

### NFS ストレージを追加した結果
{: #vc_nsx-t_addingremovingservers-adding-nfs-storage-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. NFS ストレージを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、NFS ストレージに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した NFS ストレージがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## vCenter Server with NSX-T インスタンスからの NFS ストレージの削除
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage}

### NFS ストレージを削除する前に
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-prereq}

* VMware vSphere Web クライアントから NFS ストレージの削除を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* NFS ストレージを削除する前に、そのストレージにある VM をすべて削除したことを確認してください。
* 削除しようとしている共有が、正しい vCenter Server インスタンスと関連付けられていることを確認してください。
* クラスターの状況が**「使用可能」**でなければなりません。

### NFS ストレージを削除する手順
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、NFS ストレージを削除するクラスターをクリックします。
5. **「ストレージ」**セクションで、削除するストレージ共有を選択し、**「削除」**をクリックします。
6. **「ストレージの削除 (Remove Storage)」**ウィンドウで**「削除」**をクリックします。

### NFS ストレージを削除した結果
{: #vc_nsx-t_addingremovingservers-removing-nfs-storage-results}

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. NFS ストレージを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、NFS ストレージに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって NFS ストレージに全面的な再利用処理が施されます。

   削除した NFS ストレージについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

## 関連リンク
{: #vc_nsx-t_addingremovingservers-related}

* [vCenter Server の部品構成表](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_bom)
* [vCenter Server インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_planning)
* [vCenter Server with NSX-T インスタンスの注文](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_nsx-t_orderinginstance)
* [vCenter Server with NSX-T インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/services?topic=vmware-solutions-vc_nsx-t_addingviewingcluster#vc_nsx-t_addingviewingcluster)
* [ホストをメンテナンス モードに切り替える](https://docs.vmware.com/en/VMware-vSphere/6.0/com.vmware.vsphere.resmgmt.doc/GUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/s/article/1003212){:new_window}
