---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# 스캔 및 검토
{: #vum-scanning}

호스트, 가상 머신(VM) 및 가상 어플라이언스를 스캔할 때 기준선 및 기준선 그룹에 대해 평가하여 준수 레벨을 판별합니다. 인벤토리 오브젝트를 스캔하고 결과를 검토하여 해당 오브젝트가 기준선 및 기준선 그룹을 얼마나 준수하는지를 판별합니다. 텍스트 검색, 그룹 선택, 기준선 선택 및 준수 상태 선택에 따라 스캔 결과를 필터링할 수 있습니다. 다음과 같은 스캔을 시작할 수 있습니다.
*	**vSphere ESXi 호스트의 스캔을 수동으로 시작** - 연결된 기준선 및 기준선 그룹을 기반으로 vSphere 인벤토리의 vSphere ESXi 호스트를 스캔할 수 있습니다.
*	**가상 머신 및 가상 어플라이언스의 스캔을 수동으로 시작** - 연결된 기준선 및 기준선 그룹을 기반으로 vSphere 인벤토리의 VM 및 가상 어플라이언스를 스캔할 수 있습니다.
*	**컨테이너 오브젝트의 스캔을 수동으로 시작** - 데이터 센터 또는 데이터 센터 폴더인 컨테이너 오브젝트를 스캔하여 호스트, VM 및 가상 어플라이언스의 동시 스캔을 시작합니다.
*	**검색 스케줄** - 특정 시간이나 사용자에게 편리한 간격으로 VM, 가상 어플라이언스 및 ESXi 호스트를 스캔하도록 vSphere Web Client를 구성할 수 있습니다.

## vSphere ESXi 호스트의 스캔을 수동으로 시작
{: #vum-scanning-scan-hosts}

1. **업데이트 스캔**을 클릭하고, **패치 및 확장과 업그레이드**를 선택한 후 **확인**을 클릭하십시오.
2. 스캔이 완료되면 **중요 호스트 패치**를 선택하십시오. 아래쪽 분할창에서 **패치 수**의 숫자를 클릭하여 각 호스트의 패치 세부사항을 검토하십시오. 창에 패치 정보가 표시됩니다.
3. 검토한 후 **중요하지 않은 패치**에 대해 반복하십시오.

  VUM 로그 파일은 _/var/log/vmware/vmware-updatemgr/vum-server/vmware-vum-server-log4cpp.log_ 경로에 있습니다.

## 가상 머신 및 가상 어플라이언스의 스캔을 수동으로 시작
{: #vum-scanning-scan-vm-va}

연결된 기준선 및 기준선 그룹을 기반으로 vSphere 인벤토리의 VM 및 가상 어플라이언스를 스캔할 수 있습니다. 선택한 VM 및 어플라이언스가 선택한 옵션에 따라 연결된 기준선에 대해 스캔됩니다. 모든 하위 오브젝트가 스캔되므로 가상 인프라의 규모가 크고 스캔을 시작하는 오브젝트 계층이 높을수록 스캔 시간이 더 길어지고 준수 보기의 정확성이 높아집니다.

1.	vSphere Web Client를 사용하여 **홈** > **VM 및 템플리트**를 선택하십시오.
2.	_가상 머신_, _가상 어플라이언스_ 또는 _가상 머신 및 어플라이언스의 폴더_를 마우스 오른쪽 단추로 클릭하고 **업데이트 스캔**을 클릭하십시오.
3.	스캔할 업데이트의 유형을 선택하십시오. 옵션에는 _가상 어플라이언스 업그레이드, VM 하드웨어 업그레이드_ 및 _VMware Tools 업그레이드_가 있습니다.
4.	**스캔**을 클릭하십시오.

##	컨테이너 오브젝트의 스캔을 수동으로 시작
{: #vum-scanning-scan-container}

데이터 센터 또는 데이터 센터 폴더인 컨테이너 오브젝트를 스캔하여 호스트, VM 및 가상 어플라이언스의 동시 스캔을 시작합니다.
1.	vSphere Web Client를 사용하여 **홈** > **VM 및 템플리트**를 선택하십시오.
2.	_데이터 센터_ 또는 _데이터 센터 폴더_를 마우스 오른쪽 단추로 클릭하고 **업데이트 스캔**을 클릭하십시오.
3.	스캔할 업데이트의 유형을 선택하십시오. 옵션에는 _가상 어플라이언스 업그레이드, VM 하드웨어 업그레이드_ 및 _VMware Tools 업그레이드_가 있습니다.
4.	**스캔**을 클릭하십시오.

##	스캔 스케줄
{: #vum-scanning-schedule}

특정 시간이나 사용자에게 편리한 간격으로 VM, 가상 어플라이언스 및 vSphere ESXi 호스트를 스캔하도록 vSphere Web Client를 구성할 수 있습니다.

1.	vSphere Web Client를 사용하여 인벤토리에서 오브젝트를 선택하십시오. 선택한 오브젝트의 모든 하위 오브젝트도 스캔됩니다.
2.	**모니터** 탭을 선택하고 **태스크 및 이벤트**를 클릭하십시오.
3.	**스케줄된 태스크**를 선택하고 **새 태스크 스케줄**을 클릭하십시오.
4.	표시되는 드롭 다운 목록에서 **업데이트 스캔**을 선택하십시오. 업데이트 스캔 마법사가 열립니다.
5.	설정 편집 페이지에서 인벤토리 오브젝트를 스캔할 업데이트의 유형을 선택하십시오. 하나 이상의 스캔 유형을 선택해야 합니다. 스케줄링 옵션 페이지에서 스캔 태스크에 대해 설명하고 스케줄하십시오.
6.	고유 이름을 입력하고 선택적으로 스캔 태스크에 대한 설명을 입력하십시오. **변경**을 클릭하여 스캔 태스크의 빈도 및 시작 시간을 설정하십시오. **확인**을 클릭하십시오.
7.	스캔 태스크가 vSphere Web Client의 스케줄된 태스크 보기에 나열됩니다.

## 관련 링크
{: #vum-scanning-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 디지털 기술 업무](https://ibm-dte.mybluemix.net/vmware)(데모)
