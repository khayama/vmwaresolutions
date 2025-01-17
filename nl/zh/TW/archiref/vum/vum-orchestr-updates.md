---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

#	編排的升級
{: #vum-orchestr-updates}

在更新 vSphere ESXi 主機之後，您可以使用編排的升級來升級庫存中虛擬機器的虛擬硬體及 VMware Tools。更新主機之後，會先執行 VMware Tools 升級基準線，接著執行虛擬機器硬體升級基準線。您可以在叢集、資料夾或資料中心層次使用編排的升級。

VUM 可讓您使用基準線群組，依序執行主機及虛擬機器的編排升級。使用的基準線群組包含單一主機升級基準線，以及多個修補程式或延伸規格基準線。VUM 會先升級主機，然後套用修補程式或延伸規格基準線。您可以使用包含下列基準線的虛擬機器基準線群組，來執行虛擬機器的編排升級：
* VM 硬體升級以符合主機
* VMware Tools 升級以符合主機

VUM 編排的升級可讓您以兩步驟處理程序升級 VCSA 中的庫存物件。首先，升級 vSphere ESXi 主機，接著升級虛擬機器。您可以在叢集層次配置這個兩步驟處理程序，或者，在個別的 vSphere ESXi 主機或虛擬機器層次配置此作業，以進行更精細地控制。

在編排的升級中，會先針對主機基準線群組（其套用修補程式、延伸規格及升級）重新修補叢集，而在升級之後，會針對包含「VM 硬體升級以符合主機」及「VMware Tools 升級以符合主機」基準線的虛擬機器升級基準線群組，重新修補叢集裡的虛擬機器。

如果基準線群組也包含升級基準線，則 VUM 會先升級 vSphere ESXi 主機，然後套用修補程式或延伸規格基準線，因為修補程式適用於特定主機版本。對於虛擬機器，會先更新 VMware Tools，接著更新虛擬硬體。

因此，在 VMware Tools 升級期間，如果虛擬機器處於已關閉電源或已暫停狀態，則會開啟虛擬機器的電源，接著 VUM 會開啟它的電源，並執行升級，然後還原虛擬機器的原始電源狀態。因此，在虛擬硬體升級期間，如果有已開啟電源的虛擬機器，則 VM 必須處於已電源關閉狀態，接著 VUM 會關閉它們的電源，升級虛擬硬體，然後重新開啟其電源。

依預設，vSphere ESXi 主機的補救會循序進行，而且一次重新修補一部主機。某部主機的處理程序完成時，VUM 會開始重新修補下一部主機。可以變更此預設值來啟用平行補救，以同時重新修補多部主機，不過，只有在叢集裡有足夠的失效接手容量時，才能這麼做。

如果 vSphere ESXI 主機是 vSAN 叢集的一部分，則即使您已在補救精靈中選取平行補救，補救處理程序還是一律會循序進行，因為 vSAN 叢集裡一次只能有一部主機隨時處於維護模式。VUM 是智慧型的，並會計算在不需要中斷 DRS 設定的情況下可平行重新修補的主機數目。

或者，您也可以定義在補救精靈期間可平行重新修補的主機數目限制。

下列工作流程說明執行編排升級的處理程序：

## 步驟 1
{: #vum-orchestr-updates-step1}

1. 使用 vSphere Web Client 登入 VCSA。
2. 選取**首頁** > **Update Manager**，從**物件**標籤中選取 **Update Manager 實例**。
3. 按一下**管理**標籤，然後依序按一下**主機基準線**標籤及**新建基準線群組**。
4. 輸入基準線群組的唯一名稱，然後按**下一步**。
5. 選取要內含在基準線群組中的主機升級基準線。
6. 可選擇按一下「升級」頁面底端的**建立新的主機升級基準線**來建立新的主機升級基準線，並完成「新建基準線」精靈。按**下一步**。
7. 選取要內含在基準線群組中的修補程式基準線。
8. 可選擇按一下「修補程式」頁面底端的**建立新的主機修補程式基準線**來建立新的修補程式基準線，並完成「新建基準線」精靈。按**下一步**。
9. 選取要內含在基準線群組中的延伸規格基準線。
10. 可選擇按一下「修補程式」頁面底端的**建立新的延伸規格基準線**來建立新的延伸規格基準線，並完成「新建基準線」精靈。
11. 檢閱**準備完成**頁面，按一下**完成**，「基準線群組」窗格中即會顯示主機基準線群組。

## 步驟 2
{: #vum-orchestr-updates-step2}

1. 建立包含「VMware Tools 升級以符合主機」基準線及「VM 硬體升級以符合主機」基準線的虛擬機器基準線群組（「VUM 管理」視圖）。
2. 將基準線群組連接至包含您要升級之虛擬機器的 vCenter 容器物件。
3. 掃描容器物件，以檢視容器中虛擬機器的法規遵循狀態。您可以手動啟動掃描，或排定掃描作業。
4. 檢閱「VUM 用戶端法規遵循」視圖中所顯示的掃描結果。
5. 重新修補容器物件中不合規的虛擬機器，讓它們符合所連接基準線群組的標準。您可以手動啟動補救，或排定補救作業。
* 在升級 VMware Tools 期間，必須開啟虛擬機器的電源。如果虛擬機器在補救之前處於已關閉電源或已暫停狀態，則 VUM 會開啟機器的電源。升級完成之後，VUM 會重新啟動機器，並還原虛擬機器的原始電源狀態。
* 在虛擬機器硬體升級期間，必須關閉虛擬機器。補救完成之後，VUM 會還原虛擬機器的原始電源狀態。如果開啟虛擬機器的電源，則 VUM 會關閉機器的電源，升級虛擬硬體，然後開啟虛擬機器的電源。

現在，您可以在掃描、檢閱、編譯打包及補救處理程序中使用這些基準線群組。

## 相關鏈結
{: #vum-orchestr-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 解決方案架構](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} Digital Technical Engagement](https://ibm-dte.mybluemix.net/vmware)（示範）
