---

copyright:

  years:  2016, 2019

lastupdated: "2019-05-06"

subcollection: vmware-solutions


---

# 初期構成
{: #vum-init-config}

{{site.data.keyword.vmwaresolutions_full}} 自動化により、{{site.data.keyword.cloud}} Backend Customer Router (BCR) に設定されたデフォルト・ゲートウェイを使用して VCSA が構成されます。 ただし、BCR を介したインターネットへの経路はありません。 VMware vCenter Server on {{site.data.keyword.cloud_notm}} インスタンスからインターネットへの標準経路では、管理 ESG を経由します。 VCSA または管理 ESG の構成を変更することはお勧めしません。VUM を有効にするには、カスタマー・サブネットのプロキシー・サーバー実装をお勧めします。

この方法では、VCSA または管理 ESG を再構成する必要はありませんが、小さい仮想マシン (VM) またはアプライアンスをインストールする必要があります。 プロキシー・サーバーは、2 つのエンドポイント・デバイス間に存在し、中間デバイスとして機能するシステムです。 この場合、これは VUM と VMware の更新サーバーの間に存在します。

VUM が VMware の更新サーバーからリソースを要求すると、まず要求がプロキシー・サーバーに送信され、プロキシー・サーバーからその要求が更新サーバーに送信されます。 プロキシー・サーバーによってリソースが取得されると、そのリソースは VUM に送信されます。 プロキシー・サーバーは、セキュリティー、管理制御、およびキャッシング・サービスを容易にするために使用できます。

CentOS および Squid に基づくプロキシー・サーバーを使用できます。 Squid プロキシーは、Web 用のオープン・ソース・キャッシング・プロキシーであり、HTTP や HTTPS などの多くのプロトコルをサポートします。 使用可能な VM およびアプライアンス・ベースのプロキシーは多数あり、企業の要件に基づいて適切なプロキシーを選択し、ベンダーのガイダンスに従ってインストールおよび構成する必要があります。 CentOS/Squid 実装を使用することを選択するクライアントでは、以下のプロセスに進む必要があります。

* CentOS ISO のジャンプ・サーバーへのダウンロード
* vCenter ライブラリーの作成
* ISO の vCenter ライブラリーへのアップロード
* VM の作成、CentOS のインストールと構成、および Squid のインストール

## サブネット情報の検索
{: #vum-init-config-subnet}

このタスクを開始する前に、以下の表に取り込むために情報を収集してください。 推奨値を確認し、それらがご使用の環境にとって適切な値になるようにします。 この構成は、CentOS-Minimal および Squid を使用する VUM 専用の小さいプロキシーに基づいています。

お客様のプライベート・ポータブル・サブネットを確認するには、次のようにします。

1. {{site.data.keyword.vmwaresolutions_short}} コンソールの**「リソース」**ページに進みます。
2. 必要な**「インスタンス」**を選択し、**「インフラストラクチャー」**を選択してから、**「クラスター」**を選択します。
3. **「プライベート VLAN」**を選択し、`Private subnet for customer workload edge` というラベルのサブネットを見つけます。
4. **「サブネット」**を選択すると、IP アドレスとその割り振りが表示されるサブネットの詳細ページに転送されます。
5. この情報を使用して、未割り振りの IP アドレスを選択し、**「メモ」**を該当するコメントで更新します。 この IP アドレスを以下の表の `proxy ip` パラメーターに使用します。

表 1. デプロイメント値

| パラメーター | 推奨値 | メモ |
|:--------- |:-------------- |:------ |
| プロキシー CPU | 1 つの vCPU | Squid に最小要件はありません |
| プロキシー RAM | 2 GB | Squid に最小要件はありません |
| プロキシー・ディスク | 25 | GB Squid に最小要件はありません |
| ホスト名 | Proxy01 | |
| アドレス | proxy ip | 予備の IP アドレスは、プロビジョニング・プロセス中に割り当てられた顧客のプライベート・ポータブル・サブネットから使用する必要があります。 このサブネットで予約されている IP アドレスは 2 つのみです。1 つは BCR 用で、もう 1 つは customer-esg 用です。
| ネットマスク | 255.255.255.192 | |
| ゲートウェイ| customer-nsx-edge プライベート・アップリンク IP | これは、customer-nsx-edge のプライベート・アップリンク IP アドレスであるプロキシー・サーバーのデフォルトのゲートウェイ設定です。 この IP アドレスは **customer-nsx-edge** の**「設定」**タブで確認できます。 |
| DNS サーバー | AD/DNS ip | この IP アドレスは、{{site.data.keyword.vmwaresolutions_short}} コンソールのインスタンス・ページである**「リソース」**ページにあります。 |
| BCR IP | bcr ip | これは、{{site.data.keyword.cloud_notm}} Backend Customer Router の IP アドレスであり、10.0.0.0/8 および 161.26.0.0/16 のゲートウェイです。 このアドレスは、VCSA および AD/DNS サーバーに到達できるように、プロキシー・サーバーの静的ルートで使用されます。 |

## NSX の構成
{: #vum-init-config-config-nsx}

プロキシー・サーバー・トラフィックを有効にするには、NSX カスタマー ESG ファイアウォールおよび NAT 設定が必要です。

### ファイアウォール
{: #vum-init-config-firewall}

1. **「Home」**>**「Networking & Security」**に移動します。
2. **「NSX Edges」**、「customer-nsx-edge」、**「Firewall」**の順に選択します。
3. **「+」**記号をクリックして、ファイアウォール・ルールを追加します。
4. 以下の表に示す必須パラメーターを指定します。 新しいファイアウォール・ルールは、デフォルトの拒否ルールである最後のルールの前に配置する必要があります。

表 2.ファイアウォール・ルール

| パラメーター | 推奨値 |
|:--------- |:-------------- |
| 名前 | Outbound Proxy01 |
| タイプ | ユーザー |
| ソース | proxy server ip |
| 宛先 | 任意 |
| サービス | HTTP/HTTPS/ICMP Echo |
| アクション | Accept |

パラメーターを指定したら、**「Publish Changes」**をクリックします。

### NAT
{: #vum-init-config-nat}

1. **「NAT」**を選択します。
2. **「+」**記号をクリックして、SNAT ルールを追加します。
3. 以下の表に示す必須パラメーターを指定し、**「OK」**をクリックします。 次に、**「Publish Changes」**をクリックします。

表 3. NAT ルール

| パラメーター | 推奨値 |
|:--------- |:-------------- |
| ルール・タイプ | USER |
| アクション | SNAT |
| 適用先 | パブリック・アップリンク |
| 元のプロトコル | 任意 |
| 元のソース IP | proxy server ip |
| 元のソース・ポート | 任意 |
| 元の宛先 IP | 任意 |
| 元の宛先ポート | 任意 |
| 変換済み IP アドレス | NAT ip |
| 変換済みポート範囲 | 任意 |
| 状況 | 有効化 |
| ロギング | 有効化 |
| 説明 | Proxy01 SNAT |

### プロキシー・サーバーのインストールおよび構成
{: #vum-init-config-inst-cfg-proxy}

以下のプロセスでは、コンテンツ・ライブラリーから CentOS および Squid をホストする VM をデプロイします。このプロセスは、以下のステップで構成されています。 これは、ジャンプボックスとして使用するために Windows VSI がプロビジョンされており、リモート・デスクトップ・プロトコルを使用して VSI のパブリック・インターフェースに接続していることを前提としています。

* CentOS-Minimal ISO ファイルのダウンロード
* vCenter コンテンツ・ライブラリーの構成およびそのライブラリーへの CentOS ISO ファイルの取り込み
* プロキシー VM の構成および CentOS と Squid のインストール

### CentOS-Minimal ISO ファイルのダウンロード
{: #vum-init-config-downloading-centos}

ジャンプ・サーバーのブラウザーを使用して、[CentOS](https://www.centos.org/download/) から CentOS-Minimal ISO ファイルをダウンロードします。 {{site.data.keyword.cloud_notm}} では、多くの一般的な Linux ディストリビューションのミラーが維持されることに注意してください。 このミラーはプライベート・ネットワークでのみ使用可能であり、CentOS ISO は `http://mirrors.service.softlayer.com/centos/7/isos/x86_64/` のアドレスで入手できます。

### コンテンツ・ライブラリーの構成およびそのライブラリーへの CentOS ISO ファイルの取り込み
{: #vum-init-config-config-conent-library}

ローカルの vCenter コンテンツ・ライブラリーを作成します。 ライブラリーは、それが作成された vCenter Server インスタンスでのみアクセス可能です。 VM のデプロイに必要なテンプレートおよび ISO をライブラリーに取り込みます。

1. vSphere Web Client から、**「Home」**>**「Content library」**>**「Objects」**>**「Create a new content library」**>**「Create subscribed library on the vCenter」**にナビゲートします。
2. コンテンツ・ライブラリーの名前 (例えば、ISO) を入力し、「Notes」テキスト・ボックスにライブラリーの説明を入力し、**「Next」**をクリックします。
3. **「Local content library」**を選択して、**「Next」**をクリックします。
4. データ・ストアを選択してから、適切なデータ・ストア (例えば、`vsanDatastore`) をクリックします。
5. **「Ready to Complete」**ページの情報を確認し、**「Finish」**をクリックします。

### プロキシー VM の構成および CentOS と Squid のインストール
{: #vum-init-config-config-proxy}

このアクティビティーには次のタスクがあります。

*	新規 VM の作成
*	CentOS のインストール
*	Squid のインストール

#### 新規 VM の作成
{: #vum-init-config-create-new-vm}

このタスクでは、プロキシー・サーバーとして使用できる新しい VM を作成します。 『表 1 デプロイメント値』の設定を使用して、構成にデータを設定します。

1.	vSphere Web Client から、**「Home」**>**「VMs and Templates」**にナビゲートします。
2.	「Navigator」ペインで、**「datacenter1」**をクリックし、右クリックして**「New Virtual Machine」**>**「New Virtual Machine」**を選択します。
3.	**「Create a new Virtual Machine」**を選択して、**「Next」**をクリックします。
4.	VM の名前 (例えば、Proxy01) を入力し、**「datacenter1」**を選択し、**「Next」**をクリックします。
5.	**「cluster1」**を選択して、**「Next」**をクリックします。
6.	該当するデータ・ストア (例えば、vsanDatastore) を選択し、**「Next」**をクリックして、再度**「Next」**をクリックします。
7.	**「Guest OS Family」**で**「Linux」**を選択して、**「Guest OS version」**で**「CentOS 7 (64-bit)」**を選択し、**「Next」**をクリックします。
8.	仮想ハードウェアの**「Customized Hardware」**タブで、**「CPU」を 1**、 **「Memory」を 2048 MB**、**「New Hard disk」を 25 GB** に設定します。 **「New CD/DVD drive」**で、**「Content Library ISO File」**、**「CentOS-7-x86_64-Minimal」**と選択して**「OK」**をクリックし、**「Connected」**ボックスにチェック・マークを付けます。
9.	「New device」ボックスで、**「Network」**を選択して、**「Add」**をクリックします。
10.	**「SDDC-DPortGroup-Mgmt」**ネットワークを選択して、「Connect」チェック・ボックスにチェック・マークが付いている状態にして、**「Next」**をクリックします。
11.	確認して**「Finish」**をクリックします。

#### CentOS のインストール
{: #vum-init-config-install-centos}

このタスクでは、新規作成の VM をインストールして、Squid のインストールの準備ができた状態に構成します。

1.	vSphere Web Client の「Navigator」ペインで、先ほど作成した **VM** の「Proxy01」を選択して、**「Summary」**タブを選択します。
2.	**「Play」**をクリックして VM をパワーオンします。
3.	VM がパワーオンし、CentOS 7 ISO からブートします。 VM に対して**リモート・コンソールまたは Web コンソール**を始動します。 リモート・コンソールをインストールし、Web ブラウザーを実行しているシステムで vSphere ESXi ホストを名前で解決する必要があります。
4.	「Welcome to CentOS 7」画面で、必要な言語を選択し、**「Continue」**をクリックします。
5.	**「LOCALIZATION」**画面で、**「DATE & TIME」**をクリックして、タイム・ゾーンを選択し、**「Done」**をクリックします。
6.	**「LOCALIZATION」**画面で、必要に応じて**「KEYBOARD」**をクリックしてデフォルトから変更し、**「Done」**を押します。
7.	**「LOCALIZATION」**画面で、**「INSTALLATION DESTINATION」**をクリックして、**VMware 仮想ディスク・アイコン**をクリックし、**「Done」**をクリックします。
8.	**「LOCALIZATION」**画面で、**「NETWORK & HOSTNAME」**をクリックして、ホスト名を選択したホスト名 (例えば、Proxy01) に変更します。
9.	**「Configure」**をクリックしてから**「IPv4 Settings」**をクリックします。 **「Method」**ボックスで**「Manual」**を選択します。
10.	**「Add」**ボタンを使用して、_『表 1 – デプロイメント値』_ から、_アドレス、ネットマスク_、および_ゲートウェイ_ を挿入します。
11.	『表 1 - デプロイメント値』の _DNS サーバーの IP アドレス_ を入力します。
12.	**「Routes」**ボタンをクリックして、『表 1 デプロイメント値』の _BCR IP アドレス_ のゲートウェイ IP アドレスをゲートウェイとして使用して _10.0.0.0/8 および 161.26.0.0/16_ の静的ルートを追加します。 この静的ルートにより、プロキシー・サーバーは DNS サーバーに到達できます。
13.	**「Save」**をクリックし、イーサネット・インターフェースがオンで接続済みと表示されている状態にします。 **「Done」**、**「Begin Installation」**とクリックします。
14.	インストールが続く中で、root パスワードを設定し、ユーザーをセットアップします。
15.	インストールが完了したら、ユーザーとしてログインし、コマンド _ping vmware.com_ を入力します。 名前が IP アドレスに解決されて、応答を受信します。 応答を受信しない場合は、IP アドレス、ファイアウォール・ルール、および NAT 設定を確認します。

#### Squid のインストールと構成
{: #vum-init-config-install-cfg-squid}

Squid には最小ハードウェア要件はありませんが、RAM の量は、プロキシーを介してインターネットにアクセスするユーザー、およびキャッシュに保管されているオブジェクトによって異なる場合があります。 プロキシー・サーバーは VUM によってのみアクセスされ、キャッシュが有効になっていないため、小さい VM のみが構成されます。

1. vSphere Web Client から Web コンソールまたはリモート・コンソールを使用して、ユーザーとしてプロキシー・サーバーにログインし、`su` コマンドで root に切り替えます。
2. パッケージをインストールする前に、以下のコマンドを使用してシステムおよびパッケージを更新する必要があります:
  `yum -y update`

3. デフォルトの yum リポジトリーでは Squid を使用できないため、Squid をインストールするには、EPEL リポジトリーをシステムにインストールする必要があります。 以下のコマンドを実行して EPEL リポジトリーをインストールします。
  `yum -y install epel-release`

4. 以下のコマンドを使用して更新およびクリーンアップします。

  `yum -y update`
  `yum clean all`

5. Squid は、コマンド `yum -y install squid` を使用してインストールされます。
6. インストールされたら、コマンド `systemctl start squid` を使用して Squid を即時に始動します。
7. ブート時に Squid を自動的に始動するには、コマンド `systemctl enable squid` を実行します。
8. コマンド `systemctl status squid` を実行して Squid が実行中であることを確認します。
9. コマンド `firewall-cmd –add-port=3128/tcp –permanent` を使用して、CentOS ファイアウォールで Squid ポート TCP 3128 へのアクセスを許可する必要があります。
10. ルールを保存してサービスを再始動するには、コマンド `firewall-cmd –reload` を使用します。

## VUM の初期セットアップ
{: #vum-init-config-init-setup-vum}

プロキシー・サーバーを使用してインターネット上のリポジトリーにアクセスするように VUM を構成します。
1. vSphere Web Client を使用して、**「Home」**>**「Update Manager」**にナビゲートします。 vCenter Server をクリックします。
2. **「Manage」**タブを選択して、**「Settings」**をクリックします。
3. **「Download Settings」**を選択して、_「Proxy settings」_ で**「Edit」**をクリックします。
4. **「Use Proxy」**ボックスにチェック・マークを付けて、_プロキシー・サーバーの IP アドレス_ と_ポート 3128_ を入力して、**「OK」**をクリックします。 接続状況が_「Validating」_、_「Connected」_ と変わります。
    **注**: プロキシー・サーバーへの接続をテスト中に ``Some URLs have been accessed successfully, but others are inaccessible`` というメッセージを受信しても気にしないでください。
5. **「今すぐダウンロード」**をクリックします。 _「Recent Tasks」_ ペインでこのアクティビティーが完了したことを確認します。
6. このアクティビティーが失敗した場合は、vCenter Server Appliance (vCSA) をリブートします。
  1. `https://vcsaFQDN:5480` で **root** として vCSA 管理インターフェースにログインします。
  2. **「サマリー」**をクリックし、**「リブート」**をクリックします。
  3. 確認ボックスで、**「はい」**をクリックして操作を確認します。

## 関連リンク
{: #vum-init-config-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)
