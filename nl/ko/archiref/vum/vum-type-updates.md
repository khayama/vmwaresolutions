---

copyright:

  years:  2016, 2019

lastupdated: "2019-04-25"

subcollection: vmware-solutions


---

# VMware 소프트웨어 업데이트 유형
{: #vum-type-updates}

VMware에서는 다음 용어를 사용하여 소프트웨어 업데이트에 대해 설명합니다.

표 1. VMware 소프트웨어 업데이트 용어 및 정의

|용어 |정의 |
|:------- |:----------- |
|공지 |	하나 이상의 VIB로 구성된 그룹입니다. 공지는 메타데이터 내에 정의됩니다. |
|저장소 |	온라인으로 게시되는 VIB 및 관련 메타데이터의 논리 그룹입니다. |
|호스트 업그레이드 이미지 |	Update Manager 저장소에서 가져와서 ESXi 5.5 또는 ESXi 6.0 호스트를 ESXi 6.5로 업그레이드하는 데 사용할 수 있는 ESXi 이미지입니다. |
|확장 | 	ESXi 호스트에 선택적 컴포넌트를 추가하기 위한 VIB 그룹을 정의하는 공지입니다. 일반적으로 확장은 해당 확장의 패치 또는 업데이트에 대한 책임이 있는 서드파티에서 제공합니다. |
|메타데이터 |	종속성 정보, 텍스트 설명, 시스템 요구사항 및 공지를 정의하는 추가 데이터입니다. |
|오프라인 번들 압축 파일 |	오프라인 패치 적용에 유용한 자체 포함 패키지에 VIB 및 해당 메타데이터를 캡슐화하는 아카이브입니다. ESXi 5.x 또는 ESXi 6.0에서 ESXi 6.5로의 호스트 업그레이드에는 서드파티 오프라인 번들 또는 사용자 정의 VIB 세트에서 생성한 오프라인 번들을 사용할 수 없습니다. |
|패치 |	특정 문제 또는 개선사항을 처리하기 위해 하나 이상의 VIB를 함께 그룹화한 공지입니다. |
|롤업 |	다운로드 및 배치를 용이하게 하도록 그룹화된 패치의 콜렉션입니다. |
|VA 업그레이드 |	공급업체에서 업그레이드로 간주하는 가상 어플라이언스에 대한 업데이트입니다. |
|VIB |	VIB는 단일 소프트웨어 패키지입니다. |

## 관련 링크
{: #vum-type-updates-related}

* [VMware HCX on {{site.data.keyword.cloud_notm}} 솔루션 아키텍처](/docs/services/vmwaresolutions/services?topic=vmware-solutions-hcx-archi-intro#hcx-archi-intro)
* [VMware Solutions on {{site.data.keyword.cloud_notm}} 디지털 기술 업무](https://ibm-dte.mybluemix.net/vmware)(데모)
