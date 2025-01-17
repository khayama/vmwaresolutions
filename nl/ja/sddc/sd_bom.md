---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-12"

subcollection: vmwaresolutions


---

# Cloud Foundation の部品構成表
{: #sd_bom}

VMware Cloud Foundation インスタンスに関する部品構成表 (BOM) 情報について説明します。

## Cloud Foundation インスタンスの VLAN の BOM
{: #sd_bom-vlans}

以下の表には、Cloud Foundation の VLAN に関する BOM 情報が詳述されています。

表 1. Cloud Foundation インスタンスの VLAN に関する BOM

| VLAN      | タイプ      | 詳細      |
|:----------|:----------|:-------------|
| VLAN1     | パブリック、プライマリー | パブリック・ネットワーク・アクセス用に物理 ESXi サーバーに割り当てられます。 初期デプロイメントの後は使用されません。 インターネット・アクセスに使用できます。 |
| VLAN2     | プライベート A、プライマリー | {{site.data.keyword.cloud}} によって物理 ESXi サーバーに割り当てられます。 管理インターフェースで VMware vSphere 管理トラフィック用に使用されます。<br><br>管理コンポーネントとして機能する VM (仮想マシン) に割り当てられます。<br><br>VMware NSX VTEP (VXLAN トンネル・エンドポイント) に割り当てられます |
| VLAN3     | プライベート B、ポータブル | 使用される場合、VMware vSAN に割り当てられます。<br><br>使用される場合、VMware NFS に割り当てられます。<br><br>VMware vSphere vMotion に割り当てられます。 |

## Cloud Foundation インスタンスのソフトウェアの BOM
{: #sd_bom-software}

以下の表には、Cloud Foundation のソフトウェア・コンポーネントに関する BOM 情報が詳述されています。

表 2. Cloud Foundation インスタンスのソフトウェア・コンポーネントに関する BOM

| 製造元 | コンポーネント                                | バージョン      |
|:-------------|:-----------------------------------------|:-------------|
| VMware       | vSphere ESXi                             | 6.5 Update EP11 (ビルド 6.5.0-10719125) |
| VMware       | vCenter Server Appliance                 | 6.5 U2c (ビルド 6.5.0-9451637) |
| VMware       | Platform Services Controller             | 6.5 U2c (ビルド 6.5.0-9451637) |
| VMware       | vSAN                                     | 6.6.1        |
| VMware       | NSX for vSphere                          | 6.4.1        |
| VMware       | SDDC Manager                             | 2.4          |
| Microsoft    | Windows Server Standard Edition (64 ビット) | 2012R2       |

## ESXi サーバーの拡張構成の設定
{: #sd_bom-esxi-server-advance-config}

次の表で、ESXi サーバーで適用される拡張構成設定の概要を確認してください。 この設定は、Cloud Foundation インスタンスが以前のリリース (V2.1 以前) から V2.2 以降にデプロイ (またはアップグレード) されるかどうかによって異なります。

表 3. Cloud Foundation インスタンスとクラスターに関する ESXi サーバーの拡張構成設定

| 構成設定 | V2.2 以降に新しくデプロイする場合  | V2.1 以前からアップグレードする場合 |   
|:------------- |:------------- |:------------- |
| TCP/IP ヒープ・サイズ | **TcpipHeapSize** = 32 | 未設定 |
| TCP/IP ヒープの最大値 | **TcpipHeapMax** = 1536 | 未設定 |  
| ボリュームの最大値 | **MaxVolumes** = 256 | **/NFS/MaxVolumes** = 256、**/NFS41/MaxVolumes** = 256 |  
| ハートビートの最大失敗回数 | **HeartbeatMaxFailures** = 10 | 未設定 |  
| ハートビートの頻度 | **HeartbeatFrequency** = 12 | 未設定 |  
| ハートビートのタイムアウト | **HeartbeatTimeout** = 5 | 未設定 |
| キューの最大長 | **MaxQueueDepth** = 64 | 未設定 |
| キュー・フルのサンプル・サイズ | **QFullSampleSize** = 32 | **/Disk/QFullSampleSize** = 32 |
| キュー・フルのしきい値 | **QFullThreshold** = 8 | **/Disk/QFullThreshold** = 8 |

### メモ
{: #sd_bom-notes}

* IBM Spectrum Protect&trade; Plus on {{site.data.keyword.cloud_notm}} サービスには **MaxVolumes** 設定が必要です。このサービスは、ESXi サーバーのデフォルトの NFS マウント数を超える NFS マウントを使用する可能性があるからです。
* **「未設定」**という構成設定の値は、ESXi サーバーを再起動しないと新しい設定が自動では適用されないことを示していますが、混乱を招く可能性があります。

  ストレージ拡張が適切にサポートされるように、**未設定**の構成設定を新しい値に変更してすべてのインスタンスで統一することをお勧めします。 IBM は、{{site.data.keyword.vmwaresolutions_short}} V2.2 以降のすべてのリリースで、これらの新しい設定だけを使用してテストする予定です。

  詳しくは、[Increasing the default value that defines the maximum number of NFS mounts on an ESXi/ESX host](https://kb.vmware.com/s/article/2239) を参照してください。

## 関連リンク
{: #sd_bom-related}

* [Build numbers and versions of VMware ESXi/ESX (2143832)](https://kb.vmware.com/s/article/2143832)
* [Build numbers and versions of VMware vCenter Server (2143838)](https://kb.vmware.com/s/article/2143838)
* [{{site.data.keyword.vmwaresolutions_short}} Protection Data Sheet](https://www.ibm.com/software/reports/compatibility/clarity-reports/report/html/softwareReqsForProduct?deliverableId=236C87407E7411E6BA51E79BE9476040){:new_window}
* [Cloud Foundation の概要](/docs/services/vmwaresolutions/sddc?topic=vmware-solutions-sd_cloudfoundationoverview)
