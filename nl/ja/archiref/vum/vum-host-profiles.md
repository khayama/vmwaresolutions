---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	ホスト・プロファイル
{: #vum-host-profiles}

vCenter には、ホスト・プロファイルと呼ばれる機能があります。 この機能により、事前構成の検証された参照ホスト構成を取り込み、システム管理者がクラスター内のホスト構成を管理するのに役立つプロファイルが作成されます。 ホスト・プロファイルにより、ホスト構成および構成のコンプライアンスのための自動化された集中管理メカニズムが提供されます。 ホスト・プロファイルにより、構成を管理対象オブジェクトとして扱うことができます。管理対象オブジェクト内には、構成するパラメーター (ネットワーキング、ストレージ、セキュリティー、およびその他のホスト・レベルのパラメーター) のカタログがあります。 これらのホスト・プロファイルは、個々のホスト、クラスター、またはホスト・プロファイルに関連付けられたすべてのホストとクラスターに適用できます。

元のクラスターをデプロイした IC4VS 自動化によって追加の VMware vCenter Server on {{site.data.keyword.cloud}} vSphere ESXi ホストがデプロイされるため、ホストを手動で追加する方法よりも構成ドリフトが少なくなります。 ただし、自動化以外に、システム管理者の操作によって、異なるホスト構成になる可能性があります。 例えば、NFS ストレージが追加されたり、VLAN が追加されたりします。 ホスト・プロファイルを使用し、既存のホストを基準にしてホストの整合性を検査することで新規ホストの構成を検証するのは、{{site.data.keyword.cloud_notm}} でのこのツールの有効な活用例の 1 つです。

vCenter Server クラスターにさらにホストを追加するには、[vCenter Server インスタンスの容量の拡張と縮小](/docs/services/vmwaresolutions/vcenter?topic=vmware-solutions-vc_addingremovingservers)を参照してください。

注:
*	V2.1 以上でデプロイされたインスタンスまたは V2.1 以上にアップグレードしたインスタンスの場合、新しくデプロイされる ESXi サーバーとクラスターには、VMware から提供される新しい (最新とは限りません) ESXi 更新が適用されます。
*	新しくデプロイした ESXi サーバーとクラスターに、必要な最新の更新がすべて適用されていることを確認する作業を含め、VMware コンポーネントのその他のすべての更新はお客様が行ってください。

新規ホストがクラスターに追加された後、それを保守モードにして、ワークロードをホストする前にコンプライアンス・ドリフトについて確認し、修復できるようにすることをお勧めします。

コンプライアンスを検査するには、以下の手順が必要です。
1.	既存のホストからホスト・プロファイルを作成します。
2.	新規ホストをホスト・プロファイルに接続します。
3.	ホスト・プロファイルに対する新規ホストのコンプライアンスを検査します。
4.	コンプライアンスの失敗を確認し、修復します。

##	既存のホストからのホスト・プロファイルの作成
{: #vum-host-profiles-create-host-profile}

1.	vSphere Web Client ホームから、**「Policies and Profiles」**をクリックします。
2.	**「Host Profiles」**をクリックし、「Host Profiles」ビューにナビゲートします。
3.	**「Extract Profile from a Host」アイコン**をクリックします。
4.	参照ホストとして機能する既存のホストを選択し、**「Next」**をクリックします。
5.	名前を入力し、新規プロファイルの説明を入力し、**「Next」**をクリックします。
6.	新規プロファイルの要約情報を確認し、**「Finish」**をクリックします。
7.	新しいプロファイルがプロファイル・リストに表示されます。

##	新規ホストのホスト・プロファイルへの接続
{: #vum-host-profiles-attach-to-profile}

1.	「Host Profiles」メイン・ビューの**「Profile List」**から、新規ホストに適用するために以前に作成されたホスト・プロファイルを選択します。
2.	**「Attach/Detach a host profile to hosts and clusters」アイコン**をクリックします。
3.	展開されたリストから新規ホストを選択し、**「Attach」**をクリックします。
4.	新規ホストが「Attached Entities」リストに追加されます。
5.	**「Next」**をクリックしてから、**「Finish」**をクリックします。

##	ホスト・プロファイルに対する新規ホストのコンプライアンスの検査
{: #vum-host-profiles-check-compliance}

1.	以前に作成されたホスト・プロファイルにナビゲートします。
2.	**「Check Host Profile Compliance」アイコン**をクリックします。
3.	**「Objects」**タブでコンプライアンス状況が_「Compliant」、「Unknown」、または_「Non-compliant_」に更新されます。 非準拠状況は、プロファイルと新規ホストの間に特定の不整合が検出されたことを示します。

##	コンプライアンスの失敗の確認と修復
{: #vum-host-profiles-review-compliance}

1. コンプライアンスの失敗の詳細を表示するには、準拠性検査で使用される**「Objects」**タブから**「Host Profile」**を選択します。
2. コンプライアンスが失敗したホストとホスト・プロファイルで異なるパラメーターに関する特定の詳細を表示するには、**「Monitor」**タブをクリックし、**コンプライアンス**・ビューを選択します。
3. オブジェクト階層を展開し、失敗したホストを選択します。
4. さまざまなパラメーターが、階層の下のコンプライアンス・ウィンドウに表示されます。
5. パラメーターを確認し、新規ホストが基準ホストと異なる理由を把握します。 コンプライアンスが許容されないパラメーターについては、新規ホストを保守モードから移行する前に修復します。 例えば、システム管理者の操作によって構成のドリフトが生じた箇所などです。

## 関連リンク
{: #vum-host-profiles-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)
