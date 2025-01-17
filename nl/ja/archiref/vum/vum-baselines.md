---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-29"

subcollection: vmware-solutions


---

# ベースラインの作成とインベントリー・オブジェクトへの添付
{: #vum-baselines}

ベースラインには、1 つ以上のパッチ、拡張、サービス・パック、バグ修正、またはアップグレードのコレクションが含まれ、パッチ・ベースライン、拡張ベースライン、またはアップグレード・ベースラインとして分類できます。 ベースライン・グループは、既存のベースラインを集めたものです。 ホストのベースライン・グループには、単一のアップグレード・ベースラインと、さまざまなパッチ・ベースラインおよび拡張ベースラインを含めることができます。 仮想マシンおよび仮想アプライアンスのベースライン・グループには、最大 3 つのアップグレード・ベースライン (VMware Tools のアップグレード・ベースライン 1 つ、仮想マシン・ハードウェアのアップグレード・ベースライン 1 つ、仮想アプライアンスのアップグレード・ベースライン 1 つ) を含めることができます。

VMware Update Manager (VUM) には、編集も削除もできない事前定義ベースラインが含まれています。 事前定義ベースラインを使用することも、基準を満たすパッチ・ベースライン、拡張ベースライン、およびアップグレード・ベースラインを作成することもできます。 作成するカスタム・ベースラインと事前定義ベースラインは、ベースライン・グループで結合できます。

VUM には、以下のいずれかのデバイスをスキャンして、環境内のホストが最新のパッチで更新されているかどうか、または仮想アプライアンスと仮想マシンが最新バージョンにアップグレードされているかどうかを判別するために使用できるデフォルトのベースラインが含まれています。
* すべての仮想マシン
* すべての仮想アプライアンス
* すべてのホスト

これらの事前定義ベースラインは以下のとおりです。
* **重要度の高いホスト・パッチ (事前定義済み)** - 重要度の高いパッチすべてに対する ESXi ホストのコンプライアンス状態をチェックします。
* **重要度の低いホスト・パッチ (事前定義済み)** - オプションのパッチすべてに対する ESXi ホストのコンプライアンス状態をチェックします。
* **ホストと整合するように VMware Tools をアップグレード (事前定義済み)** - ホスト上の最新バージョンの VMware Tools に対する仮想マシンのコンプライアンス状態をチェックします。 Update Manager は、ESXi 5.5.x 以降を実行しているホスト上の仮想マシンに対する VMware Tools のアップグレードをサポートします。
* **ホストと整合するように仮想マシン・ハードウェアをアップグレード (事前定義済み)** ホストがサポートする最新バージョンに対する仮想マシンの仮想ハードウェアのコンプライアンス状態をチェックします。 Update Manager は、ESXi 6.5 を実行しているホスト上での、仮想ハードウェア・バージョン vmx-13 へのアップグレードをサポートします。
* **仮想アプライアンスを最新版へアップグレード (事前定義済み)** - 最新の仮想アプライアンス・リリースのバージョンに対する仮想アプライアンスのコンプライアンス状態をチェックします。

ベースラインおよびベースライン・グループを使用するには、コンテナー・オブジェクト、仮想マシン、仮想アプライアンス、ホストなどの選択したインベントリー・オブジェクトに添付する必要があります。 ベースラインおよびベースライン・グループは個々のオブジェクトに添付できますが、フォルダー、vApp、クラスター、データ・センターなどのコンテナー・オブジェクトに添付する方が効率的です。 このステップでは、クラスター内のホストに対して事前定義ベースラインを使用します。

1. vSphere Web Client を使用して、**「Home」**>**「Hosts and Clusters」**に移動します。
2. スキャンするクラスター・オブジェクトをクリックします。
3. VUM に移動し、**「Attach Baseline」**をクリックし、2 つの事前定義パッチ・ベースラインを選択します。 **「OK」**をクリックします。

## 関連リンク
{: #vum-baselines-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)
