---

copyright:

  years:  2016, 2019

lastupdated: "2019-01-23"

---

{:tip: .tip}
{:note: .note}
{:important: .important}

# VMware Federal インスタンスの容量の拡張と縮小

ESXi サーバーを追加または削除して、VMware Federal インスタンスの容量をビジネス・ニーズに応じて拡張または縮小できます。

プライマリー・クラスターのストレージが vSAN である場合は、デプロイメント後に 1 つ以上の ESXi サーバーを追加して、クラスターのストレージ容量を増加できます。

この機能は、保護されていない VMware Federal インスタンスでのみ使用できます。
{:note}

## VMware Federal インスタンスへの ESXi サーバーの追加

### ESXi サーバーを追加する前に

* VMware vSphere Web クライアントから ESXi サーバーの追加を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_full}} コンソールと同期されません。
* NFS ストレージを使用する VMware Federal インスタンスには、2 つ以上の ESXi サーバーが必要です。 デフォルトのクラスターを拡張して、最大 51 台の ESXi サーバーを含められます。 デフォルト以外の各クラスターは、最大 59 台の ESXi サーバーを含むように拡張できます。
* vSAN ストレージを使用する VMware Federal インスタンスには、4 つ以上の ESXi サーバーが必要です。

## ESXi サーバーを追加する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を拡張するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを追加するクラスターをクリックします。
5. **「ESXi サーバー」**テーブルで**「追加」**をクリックします。
6. **「サーバーの追加」**ウィンドウで、追加するサーバーの数を選択し、価格リンクをクリックして見積もりコストを確認してから、**「追加」**をクリックします。

### ESXi サーバーを追加した結果

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを追加する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. リストに新しく追加した ESXi サーバーがクラスター内にない場合は、E メールかコンソールの通知を確認して、失敗に関する詳細を調べてください。

## VMware Federal インスタンスからの ESXi サーバーの削除

### ESXi サーバーを削除する前に

* VMware vSphere Web クライアントから ESXi サーバーの削除を行わないでください。 vSphere Web Client で行った変更は、{{site.data.keyword.vmwaresolutions_short}} コンソールと同期されません。
* NFS ストレージを使用する VMware Federal インスタンスには、2 つ以上の ESXi サーバーが必要であり、vSAN ストレージを使用する VMware Federal インスタンスには、4 つ以上の ESXi サーバーが必要です。
* ESXi サーバーを削除する際には、そのサーバーは保守モードになります。その後、そこで実行されているすべての仮想マシン (VM) は、vCenter Server からそのサーバーが削除される前にマイグレーションされます。 VM の再配置を最大限に制御するために、VMware vSphere Web Client を使用して、手動により、削除する ESXi サーバーを保守モードにし、サーバーで実行されている VM を移行することをお勧めします。 その後、{{site.data.keyword.vmwaresolutions_short}} コンソールを使用して ESXi サーバーを削除します。

## ESXi サーバーを削除する手順

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「デプロイ済みインスタンス」**をクリックします。
2. **「vCenter Server インスタンス」**テーブルで、容量を縮小するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。
4. **「クラスター」**テーブルで、ESXi サーバーを削除するクラスターをクリックします。
5. **「ESXi サーバー」**テーブルで、削除するサーバーを選択し、**「削除」**をクリックします。

### ESXi サーバーを削除した結果

1. インスタンス状況が**「使用可能」**から**「変更中」**に変わる間、コンソールにわずかな遅延が生じることがあります。 インスタンスにさらに変更を加える場合は、その前にこの操作が完全に完了するまでお待ちください。
2. ESXi サーバーを削除する要求の処理中であることが、E メールで通知されます。 コンソールで、ESXi サーバーに関連付けられたクラスターの状況が、**「変更中」**に変更されます。
3. {{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクル (通常 30 日) の最後に、{{site.data.keyword.cloud_notm}} インフラストラクチャーによって ESXi サーバーに全面的な再利用処理が施されます。

   削除した ESXi サーバーについては、{{site.data.keyword.cloud_notm}} インフラストラクチャーの請求サイクルが終了するまで課金されます。
   {:note}

### 関連リンク

* [VMware Federal インスタンスの要件と計画](/docs/services/vmwaresolutions/vcenter/vc_fed_planning.html)
* [VMware Federal インスタンスのクラスターの追加、表示、削除](/docs/services/vmwaresolutions/vcenter/fed_addviewdeleteclusters.html)
* [ホストをメンテナンス モードに切り替える](http://pubs.vmware.com/vsphere-60/index.jsp?topic=%2Fcom.vmware.vsphere.resmgmt.doc%2FGUID-8F705E83-6788-42D4-93DF-63A2B892367F.html){:new_window}
* [Enhanced vMotion Compatibility (EVC) processor support](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1003212){:new_window}
