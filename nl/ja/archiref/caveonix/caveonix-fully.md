---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-14"

subcollection: vmware-solutions


---

# 完全分散
{: #caveonix-fully}

追加の基本仮想マシン (VM) とスケールアウト VM は、資産の数とデータ保存要件に応じて追加されます。

表 1. 基本 - ユーザー・インターフェース

|パラメーター	|値|
|---|---|
|タイプ	|基本|
|VM の数	|2|
|vCPU	|2|
|RAM	|6 GB|
|ディスク	|60 GB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント	|UI|

表 2. 基本 - アプリケーションとプラグイン

|パラメーター	|値|
|---|---|
|タイプ	|基本|
|VM の数	|2|
|vCPU	|8|
|RAM	|16 GB|
|ディスク	|500 GB|
|OS	|CentOS 7|
|インストールされるアプリケーション・コンポーネント	|アプリ、プラグイン|

表 3. 基本 - Central Collector

|パラメーター	|値 |
|---|---|
|タイプ	|基本 |
|VM の数	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|500 GB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|Central Collector (クラスター) |

表 4. 基本 - リレーショナル・データベース

|パラメーター	|値 |
|---|---|
|タイプ	|基本 |
|VM の数	|2 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|1 TB |
|OS	C|entOS 7 |
|インストールされるアプリケーション・コンポーネント	|Relational Datastore (1 次 / 2 次) |

表 5. 基本 - Messaging Datastore

|パラメーター	|値 |
|---|---|
|タイプ	|基本 |
|VM の数	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|1 TB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|Messaging Datastore (クラスター) |

表 6. 基本 - Index Datastore (マスター・ノード)

|パラメーター	|値 |
|---|---|
|タイプ	|基本 |
|VM の数	|3 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|1 TB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|Index Datastore (マスター・ノード) |

表 7. データベース - Index Datastore (データ・ノード)

|パラメーター	|値 |
|---|---|
|タイプ	|基本 |
|VM の数	|5 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|4 TB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|Index Datastore (データ・ノード) |

スケールアウト VM の詳細を以下の表に説明します。

表 8. スケールアウト - データ・ノード

|パラメーター	|値 |
|---|---|
|タイプ	|スケールアウト |
|VM の数	28 |
|vCPU	|8 |
|RAM	|16 GB |
|ディスク	|4 TB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|データ・ノード (スケールアウト) |

Remote Collector VM の詳細を以下の表に示します。

表 9. Remote Collector

|パラメーター	|値 |
|---|---|
|VM の数	|必要に応じた値 |
|vCPU	|8 |
|RAM	|8 GB |
|ディスク	|1 TB |
|OS	|CentOS 7 |
|インストールされるアプリケーション・コンポーネント	|Remote Collector |

## 関連リンク
{: #caveonix-fully-related}

* [VMware vCenter Server on {{site.data.keyword.cloud}} with Hybridity Bundle](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
