---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# スキャンおよびレビュー
{: #vum-scanning}

ホスト、仮想マシン (VM)、および仮想アプライアンスをスキャンする場合は、ベースラインおよびベースライン・グループに対してそれらを評価し、それらのコンプライアンスのレベルを判別します。 インベントリー・オブジェクトがスキャンされ、結果がレビューされて、ベースラインおよびベースライン・グループにどのように準拠しているかが判別されます。 スキャン結果は、テキスト検索、グループ選択、ベースライン選択、およびコンプライアンス状況の選択によってフィルタリングできます。 以下のスキャンを開始できます。
*	**手動による vSphere ESXi ホストのスキャンの開始** - vSphere インベントリー内の vSphere ESXi ホストを、添付されたベースラインおよびベースライン・グループに対してスキャンできます。
*	**手動による仮想マシンおよび仮想アプライアンスのスキャンの開始** - vSphere インベントリー内の VM および仮想アプライアンスを、添付されたベースラインおよびベースライン・グループに対してスキャンできます。
*	**手動によるコンテナー・オブジェクトのスキャンの開始** - データ・センターまたはデータ・センター・フォルダーであるコンテナー・オブジェクトをスキャンして、ホスト、VM、および仮想アプライアンスの同時スキャンを開始します。
*	**スキャンのスケジュール** - VM、仮想アプライアンス、および ESXi ホストを特定の時間または都合の良い間隔でスキャンするように vSphere Web Client を構成できます。

## 手動による vSphere ESXi ホストのスキャンの開始
{: #vum-scanning-scan-hosts}

1. **「Scan for Updates」**をクリックして、**「Patches and Extensions and Upgrades」**を選択し、**「OK」**をクリックします。
2. スキャンが完了したら、**「クリティカル・ホスト・パッチ (Critical Host Patches)」**を選択します。 下部のペインで**「パッチ数 (Number of Patches)」**の数値をクリックして、各ホストのパッチの詳細を確認します。 ウィンドウにパッチ情報が表示されます。
3. **「Non-Critical Patches」**を確認し、繰り返します。

  VUM ログ・ファイルが置かれているパスは _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_ です。

## 手動による仮想マシンおよび仮想アプライアンスのスキャンの開始
{: #vum-scanning-scan-vm-va}

vSphere インベントリー内の VM および仮想アプライアンスを、添付されたベースラインおよびベースライン・グループに対してスキャンできます。 選択した VM およびアプライアンスは、選択したオプションに応じて、添付されたベースラインに対してスキャンされます。 すべての子オブジェクトがスキャンされるため、仮想インフラストラクチャーが大きく、スキャンを開始するオブジェクト階層が高くなるほど、スキャンにかかる時間は長く、コンプライアンス・ビューの正確性は高くなります。

1.	vSphere Web Client を使用して、**「Home」**>**「VMs and Templates」**を選択します。
2.	_仮想マシン_、_仮想アプライアンス_、または_仮想マシンおよびアプライアンスのフォルダー_ を右クリックし、**「Scan for Updates」**をクリックします。
3.	スキャン対象の更新のタイプを選択します。 オプションは、_仮想アプライアンスのアップグレード、VM ハードウェアのアップグレード_、および _VMware Tools のアップグレード_ です。
4.	**「Scan」**をクリックします。

##	手動によるコンテナー・オブジェクトのスキャンの開始
{: #vum-scanning-scan-container}

データ・センターまたはデータ・センター・フォルダーであるコンテナー・オブジェクトをスキャンして、ホスト、VM、および仮想アプライアンスの同時スキャンを開始します。
1.	vSphere Web Client を使用して、**「Home」**>**「VMs and Templates」**を選択します。
2.	_データ・センター_ または_データ・センター・フォルダー_ を右クリックして、**「Scan for Updates」**をクリックします。
3.	スキャン対象の更新のタイプを選択します。 オプションは、_仮想アプライアンスのアップグレード、VM ハードウェアのアップグレード_、および _VMware Tools のアップグレード_ です。
4.	**「Scan」**をクリックします。

##	スキャンのスケジュール
{: #vum-scanning-schedule}

VM、仮想アプライアンス、および vSphere ESXi ホストを特定の時間または都合の良い間隔でスキャンするように vSphere Web Client を構成できます。

1.	vSphere Web Client を使用して、インベントリーからオブジェクトを選択します。 選択したオブジェクトのすべての子オブジェクトもスキャンされます。
2.	**「Monitor」**タブを選択して、**「Task & Events」**をクリックします。
3.	**「Scheduled Tasks」**を選択して、**「Schedule a New Task」**をクリックします。
4.	表示されるドロップダウン・リストから**「Scan for Updates」**を選択します。 「Scan for Updates」ウィザードが開きます。
5.	「Edit Settings」ページで、インベントリー・オブジェクトをスキャンする更新のタイプを選択します。 少なくとも 1 つのスキャン・タイプを選択する必要があります。 「Scheduling options」ページで、スキャン・タスクを記述およびスケジュールします。
6.	スキャン・タスクの固有の名前、およびオプションで説明を入力します。 **「Change」**をクリックして、スキャン・タスクの頻度と開始時刻を設定します。 **「OK」**をクリックします。
7.	スキャン・タスクが vSphere Web Client の「Scheduled Tasks」ビューにリストされます。

## 関連リンク
{: #vum-scanning-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} ソリューションのアーキテクチャー](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware) (デモンストレーション)
