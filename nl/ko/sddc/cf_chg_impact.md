---

copyright:

  years:  2016, 2019

lastupdated: "2019-03-14"

subcollection: vmwaresolutions


---

{:tip: .tip}
{:note: .note}
{:important: .important}
{:faq: data-hd-content-type='faq'}

# Cloud Foundation 아티팩트 변경에 대한 고려사항
{: #cf_chg_impact}

{{site.data.keyword.vmwaresolutions_full}}에 대해 예약된 사용자, 리소스 또는 서브넷을 변경하면 VMware Cloud Foundation 인스턴스의 관리 오퍼레이션에 영향을 줄 수 있습니다.

VMware vSphere Web Client의 **사용자 및 그룹** 페이지에서 **ic4v-vCenter** 그룹의 글로벌 권한을 변경하지 마십시오. 글로벌 권한 변경에는 사용자 이름 변경, 사용자 삭제 또는 해당 비밀번호 변경이 포함됩니다.
**root** 호스트 사용자 ID 대신 **customerroot** 호스트 사용자 ID를 사용하십시오.
{:important}

## 서비스 고유 사용자 계정
{: #cf_chg_impact-service-usr-account}
{: faq}

각 서비스는 vCenter Server에 내부 사용자 계정을 작성합니다. 이 계정은 서비스와 연관된 관리 조작이 서비스에 대해 해당 조작을 수행하기 위해 vCenter Server에 연결하는 데 필요합니다.

가동 중단 및 연결 문제점을 방지하려면 이 사용자 계정의 사용자 ID, 비밀번호 또는 비밀번호 만기 설정을 변경하는 경우 연관된 서비스에서도 해당 정보를 업데이트해야 합니다.
{:important}

이 계정의 사용자 ID 형식은 `<service_name>-<truncated service_uuid>@test.local` 또는 `<service_name>-<truncated service_uuid>@example-domain.local`입니다. 예를 들어, Veeam on {{site.data.keyword.cloud_notm}} 서비스가 스케줄된 백업을 수행하기 위해 vCenter Server에 연결하는 데 사용하는 사용자 ID는 `Veeam-<Veeam_uuid>@test.local`입니다.

`<service_name>`은 `<service_uuid>`와 함께 20자에서 잘립니다.
{:note}

## Cloud Foundation 인스턴스에 대한 VMware 리소스
{: #cf_chg_impact-vmware-resources}
{: faq}

다음 표는 {{site.data.keyword.vmwaresolutions_short}} 콘솔 외부에서 VMware 리소스를 변경하는 경우 영향을 받을 수 있는 오퍼레이션을 나열합니다. 복구하기 위한 솔루션을 사용할 수 있는 경우 해당 솔루션도 제공됩니다.

표 1. SSO 관리(고객)에 대해 영향을 받은 오퍼레이션

|시도된 변경  |영향을 받은 오퍼레이션  |심각도  |복구 방법  |
|:------------- |:------------- |:--------------|:--------------|
|VMware 가상 데이터 센터 이름 변경 |새 ESXi 서버가 변경된 데이터 센터에 결합할 수 없으므로 VMware 데이터 센터 추가에 실패할 수 있음 |중요 |VMware 가상 데이터 센터 이름을 원래의 이름으로 다시 변경함 |
|포트 그룹 이름 변경    |ESXi 서버 추가에 실패할 수 있음 |중요 |포트 그룹 이름을 원래의 이름으로 다시 변경함 |
|클러스터 이름 변경 |ESXi 서버 추가에 실패할 수 있음 |중요 |클러스터 이름을 원래의 이름으로 다시 변경함
|공용 또는 사설 DVS(Distributed Virtual Switch) 이름 변경 |ESXi 서버 추가에 실패할 수 있음 |중요 |DVS 이름을 원래의 이름으로 다시 변경함
|VSAN 데이터 저장소 이름 변경 |ESXi 서버 추가에 실패할 수 있음<br><br>인스턴스 업그레이드가 실패할 수 있음 |중요 |VSAN 데이터 저장소 이름을 원래 이름인 **vsanDatastore**로 다시 변경함
|인스턴스 이름 또는 도메인 이름 변경 |인스턴스를 사용할 수 없음 |위험 |해당사항 없음

다음 표에는 다양한 리소스에 대한 SSH 또는 쉘 액세스가 사용 안함으로 설정된 경우 영향을 받을 수 있는 오퍼레이션이 나열되어 있습니다.

표 2. SSH 및 쉘 액세스(로컬)에 영향을 받은 오퍼레이션

|시도된 변경  |영향을 받은 오퍼레이션  |심각도  |복구 방법  |
|:------------- |:------------- |:--------------|:--------------|
|vCenter Server 또는 PSC에 대한 SSH 또는 쉘 액세스를 사용 안함으로 설정합니다.    |기본 및 보조 인스턴스의 페어링이 실패할 수 있습니다. 리소스에 패치를 적용하는 작업이 실패할 수 있습니다.    |중요    |해당사항 없음    |

SSH 또는 쉘 액세스를 사용 안함으로 선택하는 경우 표시된 오퍼레이션을 수행하기 전에 임시로 다시 사용으로 설정해야 합니다.

## Cloud Foundation 인스턴스에 대한 관리 서브넷
{: #cf_chg_impact-mgmt-subnets}
{: faq}

다음 정보는 {{site.data.keyword.vmwaresolutions_short}}에서 주문된 서브넷에 대해 설명하고 사용자 전용의 추가 서브넷을 주문할 수 있는 옵션을 제공합니다.

**주의:** 다른 목적으로 컴포넌트를 사용하지 마십시오. 그렇지 않으면, 환경의 안전성이 심각하게 손상될 수 있습니다.

각 {{site.data.keyword.cloud_notm}} Bare Metal Server 주문 시 기본적으로 다음 범위의 IP 주소가 주문됩니다.
*  32개 IP 주소의 기본 공용 범위
*  64개 IP 주소의 기본 개인 범위

또한 다음 관리 서브넷도 {{site.data.keyword.vmwaresolutions_short}}에 대해 예약됩니다.
*  첫 번째 VLAN에서 64개 IP 주소의 두 가지 포터블 사설 서브넷(하나는 관리용, 다른 하나는 VTEPS용)
*  두 번째 VLAN에서 64개 IP 주소의 두 가지 포터블 사설 서브넷(하나는 vMotion용, 다른 하나는 vSAN용)
*  공용 VLAN에서 16개 IP 주소의 공인 포터블 서브넷

사용할 추가 서브넷이 필요한 경우 다음 방법 중 하나로 사용할 IP 주소를 얻을 수 있습니다.
* **옵션 1(권장):** VMware NSX 가상 네트워크 오버레이를 사용하십시오. 샘플 VXLAN 템플리트는 주문 시 제공됩니다. 이 VXLAN 템플리트는 SDN을 빌드하기 위한 시작 지점으로 사용될 수 있습니다.
* **옵션 2:** 고유한 포터블 공인 또는 사설 서브넷을 주문하여 IP 주소를 가져오십시오. 주문한 서브넷을 관리 서브넷과 구별하기 위해 주문 중인 모든 서브넷에 참고사항을 추가할 수 있습니다.
