---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-07"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}

# Cloud Foundation インスタンスのクラスターの追加、表示、削除
{: #sd_addingviewingclusters}

インスタンスの注文時に構成した ESXi サーバーは、デフォルトのクラスターの下にグループ化されます。 デフォルトのクラスター名は次のとおりです。
* V2.1 以降のリリースでデプロイされたインスタンスの場合: **MGMT-Cluster-`<subdomain_label>`**
* V2.0 以前のリリースでデプロイされたインスタンスの場合: **SDDC-Cluster**

VMware Cloud Foundation インスタンスに独自のクラスターを追加して、コンピュート能力やストレージ容量を拡張できます。 クラスター内で ESXi サーバーを管理すると、リソース割り振りを改善したり高可用性を実現したりできます。 不要になった場合は、追加したクラスターをインスタンスから削除できます。

## 可用性
{: #sd_addingviewingclusters-availability}

* クラスターの追加機能は、V2.0 以降のリリースでデプロイ (または V2.0 以降のリリースにアップグレード) されたインスタンスでのみ利用できます。
* クラスターの削除機能は、V2.3 以降のリリースでデプロイ (または V2.3 以降のリリースにアップグレード) されたインスタンスでのみ利用できます。  

## Cloud Foundation インスタンスへのクラスターの追加
{: #sd_addingviewingclusters-adding}

1 つの Cloud Foundation インスタンスに最大 5 つのクラスターを追加できます。

### システム設定
{: #sd_addingviewingclusters-adding-sys-settings}

Cloud Foundation インスタンスにクラスターを追加するときには、以下の設定を指定する必要があります。

#### クラスター名
{: #sd_addingviewingclusters-adding-cluster-name}

クラスター名は、以下の要件を満たしている必要があります。
* 英数字とダッシュ (-) の文字だけを使用できます。
* クラスター名の先頭と末尾は、英数字でなければなりません。
* クラスター名の最大の長さは 30 文字です。
* クラスター名は、Cloud Foundation インスタンス内で固有でなければなりません。

#### データ・センターの場所
{: #sd_addingviewingclusters-adding-dc-location}

クラスターの {{site.data.keyword.CloudDataCent}}の場所は、デフォルトでは Cloud Foundation インスタンスの {{site.data.keyword.CloudDataCent_notm}}に設定されます。 デプロイ済みのインスタンスとは異なる {{site.data.keyword.CloudDataCent_notm}}にクラスターをデプロイできますが、それら 2 カ所の {{site.data.keyword.CloudDataCents_notm}}間のネットワーク待ち時間が、150 ms 未満になるようにしてください。 ネットワーク待ち時間を確認するには、[SoftLayer IP Backbone Looking Glass](http://lg.softlayer.com/){:new_window} などのツールを使用できます。

使用できるデータ・センターは、デプロイメントで選択したベア・メタル・サーバー構成に応じて異なります。 **「Skylake」**構成または**「Broadwell」**構成を選択すると、クラスターを別の {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポッドにデプロイすることもできます (ただし、選択したデータ・センターに他のポッドが含まれている場合)。 この構成は、初期インスタンスがデプロイされているデフォルトの {{site.data.keyword.cloud_notm}} インフラストラクチャー・ポッドが最大容量に達している場合に便利です。

クラスターを別のデータ・センターまたはポッドにデプロイする場合は、注文した{{site.data.keyword.baremetal_short}}で使用するためにさらに 3 つの VLAN を注文します。

### ベア・メタル・サーバーの設定
{: #sd_addingviewingclusters-adding-bare-metal-settings}

**「Skylake」**または**「Broadwell」**のいずれかを選択できます。

#### Skylake
{: #sd_addingviewingclusters-adding-skylake}

**「Skylake」**設定の場合、**「CPU モデル」**と**「RAM」**には複数のオプションがあります。 利用できるオプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

表 1. Skylake {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション   | RAM オプション   |
|:------------- |:------------- |
| Dual Intel Xeon Silver 4110 プロセッサー / 合計 16 コア、2.1 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 5120 Processor / 合計 28 コア、2.2 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |
| Dual Intel Xeon Gold 6140 Processor / 合計 36 コア、2.3 GHz | 128 GB、192 GB、384 GB、768 GB、1.5 TB |

#### Broadwell
{: #sd_addingviewingclusters-adding-broadwell}

**「Broadwell」**設定の場合、**「CPU モデル」**と**「RAM」**には複数のオプションがあります。 利用できるオプションは、インスタンスを最初にデプロイしたバージョンによって異なる場合があります。

表 2. Broadwell {{site.data.keyword.baremetal_short}}のオプション

| CPU モデル・オプション   | RAM オプション   |
|:------------- |:------------- |
| デュアル Intel Xeon E5-2620 v4 / 合計 16 コア、2.1 GHz | 128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2650 v4 / 合計 24 コア、2.2 GHz | 128 GB、256 GB、512 GB、768 GB、1.5 TB |
| デュアル Intel Xeon E5-2690 v4 / 合計 28 コア、2.6 GHz | 128 GB、256 GB、512 GB、768 GB、1.5 TB |
| クワッド Intel Xeon E7-4820 v4 / 合計 40 コア、1.9 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |
| クワッド Intel Xeon E7-4850 v4 / 合計 64 コア、2.2 GHz | 128 GB、256 GB、512 GB、1 TB、2 TB、3 TB |

### vSAN ストレージ設定
{: #sd_addingviewingclusters-adding-vsan-storage-settings}

**「Skylake」**および**「Broadwell」**ベアメタル・サーバー構成の場合は、以下の設定を指定して vSAN ストレージをカスタマイズできます。
* **vSAN 容量ディスクのディスク・タイプとサイズ**: 必要な容量ディスクのオプションを選択します。
* **vSAN 容量ディスクの数**: 追加する容量ディスク数を指定します。
* 容量ディスクを上限の 8 個を超えて追加する場合は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けます。 このオプションでは、合計 10 個の容量ディスクに 2 つの追加の容量ディスク・ベイが提供されますので、より少ない待ち時間とより高い IOPS スループットが求められるワークロードを扱うときに役立ちます。

  **High-Performance Intel Optane** オプションは、Skylake の CPU モデルの Dual Intel Xeon Gold 5120 および Dual Intel Xeon Gold 6140 でのみ使用できます。
  {:note}

* **「Disk Type for vSAN Cache Disks」**および**「Number of vSAN Cache Disks」**の値を確認します。 これらの値は、**「High-Performance Intel Optane」**ボックスにチェック・マークを付けたかどうかによって異なります。

### ライセンス交付の設定
{: #sd_addingviewingclusters-adding-licensing-settings}

クラスター内の VMware コンポーネント (VMware vSphere と VMware vSAN を含む) のライセンス・オプションを指定できます。
* IBM ビジネス・パートナーであるユーザーの場合、vSphere ライセンス (Enterprise Plus エディション) と vSAN ライセンスが自動的に含められて購入されます。 ただし、vSAN ライセンスのエディションは指定する必要があります。
* IBM ビジネス・パートナーでないユーザーの場合、**「購入に含める (Include with purchase)」**を選択してコンポーネントに IBM 提供 VMware ライセンスを使用することも、**「自分で提供する (I will provide)」**を選択し、所有するライセンス・キーを入力してライセンス持ち込み (BYOL) を適用することもできます。

## Cloud Foundation インスタンスにクラスターを追加する手順
{: #sd_addingviewingclusters-adding-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、クラスターを追加するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスにクラスターを追加できません。
   {:note}

3. 左側のナビゲーション・ペインにある**「インフラストラクチャー」**をクリックし、**「クラスター」**テーブルの右上にある**「追加」**をクリックします。
4. **「Add Cluster」**ページで、クラスター名を入力します。
5. インスタンスのホスト以外の {{site.data.keyword.CloudDataCent_notm}} でクラスターをホストする場合は、**「Bare Metal Server」**で**「Select a different location」**チェック・ボックスにチェック・マークを付けて、インスタンスをホストする {{site.data.keyword.CloudDataCent_notm}} を選択します。
6. **「CPU モデル」**と**「RAM」**のサイズを指定して、ベア・メタル構成を完了します。
7. ストレージ構成を次の手順で実行します。
   1. vSAN 容量ディスクおよびキャッシュ・ディスクのディスク・タイプとディスク数を指定します。
   2. さらにストレージが必要な場合は、**「High-Performance with Intel Optane」**チェック・ボックスを選択します。
8. ライセンス・キーの提供方法を指定します。
   * IBM ビジネス・パートナーであるユーザーの場合、vSphere ライセンス (Enterprise Plus エディション) と vSAN ライセンスが自動的に含められて購入されます。 ただし、vSAN ライセンスのエディションは指定する必要があります。
   * IBM ビジネス・パートナーでないユーザーの場合は、以下のオプションのいずれかを選択できます。
       * 新規ライセンスを自動購入する場合は、コンポーネントの**「購入に含める」**を選択します。 VMware vSAN の場合は、ライセンス・エディションも選択します。
       * 所有している VMware ライセンスをコンポーネントに使用する場合は、**「自分で提供する」**を選択し、コンポーネントのライセンス・キーを入力します。
9. **「発注要約」**ペインで、クラスター構成を確認してからクラスターを追加します。
   1. クラスターの設定を確認します。
   2. クラスターの見積もりコストを確認します。 PDF のサマリーを生成するには、**「料金詳細」**をクリックします。 注文のサマリーを保存または印刷するには、PDF ウィンドウの右上にある**「印刷」**アイコンまたは **「ダウンロード」**アイコンをクリックします。
   3. 注文に適用される使用条件のリンクをクリックして、クラスターを追加する前にそれらの条件に同意することを確認する必要があります。
   4. **「プロビジョン」**をクリックします。

### Cloud Foundation インスタンスにクラスターを追加した結果
{: #sd_addingviewingclusters-adding-results}

1. クラスターのデプロイメントが自動的に開始され、クラスターの状況が**「初期化中」**に変更されます。 デプロイメントの状況を、インスタンスのサマリー・ページでデプロイメント履歴を参照して確認できます。
2. クラスターを使用する準備ができると、状況が**「使用可能」**に変更されます。 新しく追加されたクラスターで、vSphere High Availability (HA) と vSphere Distributed Resource Scheduler (DRS) が有効になります。

クラスター名は変更できません。 クラスター名を変更すると、クラスター内の ESXi サーバーの追加または削除の操作が失敗することがあります。
{:important}

## Cloud Foundation インスタンスでクラスターを表示する手順
{: #sd_addingviewingclusters-viewing-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、クラスターを表示するインスタンスをクリックします。
3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**表で、クラスターに関する要約を表示します。
   * **名前**: クラスターの名前。
   * **ESXi サーバー**: クラスター内の ESXi サーバー数。
   * **CPU**: クラスター内の ESXi サーバーの CPU 仕様。
   * **カスタマイズ vSAN ディスク**: クラスター内の vSAN ディスクの数 (ディスク・タイプおよび容量も含む)。
   * **メモリー**: クラスター内の ESXi サーバーの合計メモリー・サイズ。
   * **データ・センターの場所**: クラスターがホストされるデータ・センター。
   * **ポッド (Pod)**: クラスターがデプロイされているポッド。
   * **状況**: クラスターの状況。 状況は、以下のいずれかの値になります。
   <dl class="dl">
       <dt class="dt dlterm">初期化中</dt>
       <dd class="dd">クラスターは作成され、構成されています。</dd>
       <dt class="dt dlterm">変更中</dt>
       <dd class="dd">クラスターは変更されています。</dd>
       <dt class="dt dlterm">使用可能</dt>
       <dd class="dd">クラスターは使用可能です。</dd>
       <dt class="dt dlterm">削除中</dt>
       <dd class="dd">クラスターは削除中です。</dd>
       <dt class="dt dlterm">削除済み</dt>
       <dd class="dd">クラスターが削除された場合。</dd>
   </dl>
   * **アクション**: **「削除」**アイコンをクリックしてクラスターを削除できます。
4. クラスター名をクリックして、ESXi サーバーのリストと各サーバーの情報を表示します。

   * **名前**: ESXi サーバーの名前は、`<host_prefix><n>.<subdomain_label>.<root_domain>` という形式です。各部の意味は次のとおりです。

      `host_prefix` はホスト名接頭部、
      `n` は ESXi サーバーの順序、
      `subdomain_label` はサブドメイン・ラベル、
      `root_domain` はルート・ドメイン・ネームです。

   * **バージョン**: ESXi サーバーのバージョン。
   * **資格情報**: ESXi サーバーにアクセスするためのユーザー名とパスワード。
   * **プライベート IP**: ESXi サーバーのプライベート IP アドレス。
   * **状況**: ESXi サーバーの状況。以下の値のいずれかになります。
        <dl class="dl">
        <dt class="dt dlterm">追加済み</dt>
        <dd class="dd">ESXi サーバーが追加され、使用可能な状態です。 </dd>
        <dt class="dt dlterm">追加中</dt>
        <dd class="dd">ESXi サーバーが追加されています。 </dd>
        <dt class="dt dlterm">削除中</dt>
        <dd class="dd">ESXi サーバーが削除されています。</dd>
        </dl>
   * vSAN ライセンスと vSphere ライセンスの詳細。 vSphere ライセンスの詳細は、クラスターの注文時に、自分で所有する VMware ライセンスを使用すること (BYOL) を選択した場合にのみ表示されます。
       * **ライセンス・タイプ**: vSAN ライセンスまたは vSphere ライセンス。
       * **注文タイプ**: ライセンスは、ユーザーが提供する (BYOL) か、自動的に購入されます。
       * **ライセンス・エディション**: ライセンスのエディション。
       * **ライセンス・キー**: ライセンス・キー。
       * **合計キャパシティー (CPU)**: ライセンスで提供される CPU の合計キャパシティーまたは合計数。
       * **空きキャパシティー (CPU)**: ライセンスで使用できるキャパシティー。

## Cloud Foundation インスタンスからのクラスターの削除
{: #sd_addingviewingclusters-deleting}

不要になったクラスターをインスタンスから削除したい場合があります。

### 削除する前に
{: #sd_addingviewingclusters-deleting-prereq}

* この手順を使用して、V2.3 以降のリリースでデプロイされたインスタンスからクラスターを削除できます。
* V2.2 以前のインスタンスでデプロイしたクラスターの場合に、インスタンスに追加したクラスターを削除するには、インスタンスを V2.3 にアップグレードする必要があります。
* クラスターは一度に 1 つしか削除できません。 複数のクラスターを削除する場合は、順番に削除する必要があります。つまり、前のクラスターが削除されるまで待ってから、次のクラスターを削除してください。
* クラスターを削除する前に、クラスター内のすべてのノードが電源オンの状態で作動可能であることを確認します。
* クラスターを削除すると、クラスターのすべての VM (仮想マシン) も削除され、復旧できなくなります。 VM を保持したい場合は、他のクラスターに移行してください。
* デフォルトのクラスターは削除できません。

## Cloud Foundation インスタンスからクラスターを削除する手順
{: #sd_addingviewingclusters-deleting-procedure}

1. {{site.data.keyword.vmwaresolutions_short}} コンソールで、左側のナビゲーション・ペインの**「リソース」**をクリックします。
2. **「Cloud Foundation インスタンス」**テーブルで、クラスターを削除するインスタンスをクリックします。

   インスタンスの状況が**「使用可能」**であることを確認してください。 そうでない場合、インスタンスからクラスターを削除できません。
   {:note}

3. 左側のナビゲーション・ペインの**「インフラストラクチャー」**をクリックします。 **「クラスター」**テーブルで、削除するクラスターを見つけて**「削除」**アイコンをクリックします。
4. 他のクラスターに VM を移行する場合は、その移行が完了したことを確認し、クラスターを削除することを確認します。

## 関連リンク
{: #sd_addingviewingclusters-related}

* [Cloud Foundation インスタンスの表示](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_viewinginstances)
* [Cloud Foundation インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_addingremovingservers)
