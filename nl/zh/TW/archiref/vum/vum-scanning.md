---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# 掃描及檢閱
{: #vum-scanning}

當您掃描主機、虛擬機器 (VM) 和虛擬應用裝置時，可以根據基準線及基準線群組來評估它們，以判斷其法規遵循層次。掃描庫存物件，並檢閱結果來判斷它們符合基準線及基準線群組的程度。可以依文字搜尋、群組選項、基準線選項及法規遵循狀態選項來過濾掃描結果。您可以起始下列掃描：
*	**手動起始 vSphere ESXi 主機的掃描** - 您可以根據連接的基準線及基準線群組，來掃描 vSphere 庫存中的 vSphere ESXi 主機。
*	**手動起始虛擬機器及虛擬應用裝置的掃描** - 您可以根據連接的基準線及基準線群組，來掃描 vSphere 庫存中的 VM 及虛擬應用裝置。
*	**手動起始容器物件的掃描** - 藉由掃描作為資料中心或資料中心資料夾的容器物件，來開始同時掃描主機、VM 及虛擬應用裝置。
*	**排定掃描** - 您可以將 vSphere Web Client 配置為在特定時間或依您方便的時間間隔來掃描 VM、虛擬應用裝置及 ESXi 主機。

## 手動起始 vSphere ESXi 主機的掃描
{: #vum-scanning-scan-hosts}

1. 按一下**掃描更新**，選取**修補程式、延伸規格及升級**，然後按一下**確定**。
2. 掃描完成時，請選取**重要主機修補程式**。在下方窗格中，按一下**修補程式數**中的數目，以檢閱每部主機的修補程式詳細資料。視窗會顯示修補程式資訊。
3. 針對**非重要修補程式**，進行檢閱並重複。

  VUM 日誌檔位於下列路徑：_/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_

## 手動起始虛擬機器及虛擬應用裝置的掃描
{: #vum-scanning-scan-vm-va}

您可以根據連接的基準線及基準線群組，來掃描 vSphere 庫存中的 VM 及虛擬應用裝置。視選取的選項而定，會針對連接的基準線掃描您所選取的 VM 及應用裝置。會掃描所有子物件，因此虛擬基礎架構越大，且您起始掃描的物件階層越高，掃描所需的時間就越長，而且法規遵循視圖就越精確。

1.	使用 vSphere Web Client，選取**首頁** > **VM 及範本**。
2.	在_虛擬機器_、_虛擬應用裝置_ 或_虛擬機器及應用裝置的資料夾_ 上按一下滑鼠右鍵，然後按一下**掃描更新**。
3.	選取要掃描的更新類型。選項為_虛擬應用裝置升級、VM 硬體升級_ 及 _VMware Tools 升級_。
4.	按一下**掃描**。

##	手動起始容器物件的掃描
{: #vum-scanning-scan-container}

藉由掃描作為資料中心或資料中心資料夾的容器物件，來開始同時掃描主機、VM 及虛擬應用裝置。
1.	使用 vSphere Web Client，選取**首頁** > **VM 及範本**。
2.	在_資料中心_ 或_資料中心資料夾_ 上按一下滑鼠右鍵，然後按一下**掃描更新**。
3.	選取要掃描的更新類型。選項為_虛擬應用裝置升級、VM 硬體升級_ 及 _VMware Tools 升級_。
4.	按一下**掃描**。

##	排定掃描
{: #vum-scanning-schedule}

您可以將 vSphere Web Client 配置為在特定時間或依您方便的時間間隔來掃描 VM、虛擬應用裝置及 vSphere ESXi 主機。

1.	使用 vSphere Web Client，選取庫存中的物件。也會掃描您所選取物件的所有子物件。
2.	選取**監視**標籤，然後按一下**作業及事件**。
3.	選取**排定的作業**，然後按一下**排定新的作業**。
4.	從出現的下拉清單中，選取**掃描更新**。即會開啟「掃描更新」精靈。
5.	在「編輯設定」頁面上，選取要掃描其庫存物件的更新類型。您必須至少選取一種掃描類型。在「排定選項」頁面上，說明並排定掃描作業。
6.	輸入掃描作業的唯一名稱及選用的說明。按一下**變更**，以設定掃描作業的頻率及開始時間。按一下**確定**。
7.	掃描作業會列在 vSphere Web Client 的「排定的作業」視圖中。

## 相關鏈結
{: #vum-scanning-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware)（示範）
