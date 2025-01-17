---

copyright:

  years:  2016, 2019

lastupdated: "2019-02-15"

subcollection: vmware-solutions


---

# 현대화 과정
{: #vcscontent-modjourney}

이는 {{site.data.keyword.cloud}} Private, IBM Middleware 컨텐츠, {{site.data.keyword.containerlong_notm}} 및 VMware vCenter Server on {{site.data.keyword.cloud_notm}}를 사용하여 클래식 WebSphere Application Server 애플리케이션을 현대화하는 방법에 대한 참조 유스 케이스입니다.

## 현대화는 애플리케이션 이상임
{: #vcscontent-modjourney-modernization}

모두가 클라우드 과정 중에 있으며 이 과정의 서로 다른 지점에 있습니다. 이 유스 케이스는 애플리케이션 설계자인 Jane과 클라우드 인프라 설계자인 Todd가 계획한 점진적 단계를 통해 기존 애플리케이션인 Stock Trader를 현대화하는 방법에 중점을 둡니다. 이 유스 케이스는 각 단계의 규모에 관계없이 과정의 각 단계를 수행하는 데 도움을 주는 예제와 비즈니스에 실현된 가치를 보여줍니다.

이 과정에서 대부분은 Stock Trader 애플리케이션을 현대화하는 것에 중점을 둡니다. 비즈니스를 클라우드 기반 비즈니스로 완전히 현대화하려면 애플리케이션, DevOps, 통합 및 관리 주제가 논의되어야
합니다. 모든 테마는 함께 작동하여 목표를 달성할 수 있도록 지원합니다. 하나의 테마(나머지 테마 없이)를 현대화하면 문제가 발생할 수 있습니다.

## 현대화하는 이유
{: #vcscontent-modjourney-reasons}

### 애플리케이션 현대화
{: #vcscontent-modjourney-app-mod}

목표는 빠르게 변화하는 요구에 맞추어 스케일링하고 응답하는 클라우드 기반 애플리케이션을 만드는 것입니다.

* 고객의 상상력을 캡처하기 위해서는 기존 앱을 현대화하고 새로운 클라우드 기반 앱을 만들어야 합니다.
* 스케일링되고, 전세계에 접근하고, 요구사항을 조정하고, 변경하고, 향상시키고, 신속하게 피벗할 수 있는 앱이 필요합니다.

### DevOps 현대화
{: #vcscontent-modjourney-devops-mod}

앱을 현대화하는 동안 해당 애플리케이션을 제공하는 방식, 즉 전체 제공 파이프라인을 현대화하여 개발자가 만들고 있는 새로운 클라우드 기반 환경을 앱 제공 방식에 맞게 확장할 수 있습니다.

* 애플리케이션을 현대화하는 동안 개발 및 운영(및 보안) 환경을 현대화해야 합니다.
* 스케일링되고, 전세계에 접근하고, 요구사항을 조정하고, 변경하고, 향상시키고, 신속하게 피벗할 수 있는 DevOps 팀이 필요합니다.

###  현대화 통합
{: #vcscontent-modjourney-integration-mod}

현대화 모든 과정에서 팀은 기존 자산, 새 클라우드 서비스, 데이터 및 해당 데이터로 수행된 분석에서 얻은 새로운 통찰과 통합해야 합니다.

* 스케일링되고, 전세계에 접근하고, 요구사항을 조정하고, 변경하고, 향상시키고, 신속하게 피벗할 수 있는 방식으로 이 과정에서 기존 자산을 사용해야 합니다.
* 이 과정의 각 단계에서 새 클라우드 서비스로 강화해야 합니다.
* 데이터에 분석을 적용함으로써 얻은 통찰과 데이터를 통합해야 합니다.

### 관리
{: #vcscontent-modjourney-mgmt}

관리 방법을 현대화하는 것은 애플리케이션을 현대화하는 동안 수행되는 다른 병렬 과정입니다. 현대화된 애플리케이션을 관리하고 유지보수하는 방법에 대한 도구, 환경 및 핵심 동작은 이전과 크게 다릅니다.

* 내장된 오케스트레이션, 로깅 및 모니터링 기능을 사용하여 마이크로서비스 및 컨테이너화된 미들웨어를 관리해야 합니다.
* 스케일링되고, 전세계에 접근하고, 요구사항을 조정하고, 변경하고, 향상시키고, 신속하게 피벗할 수 있는 방식으로 전세계의 여러 지역에 있는 다중 클라우드 하이브리드 플랫폼을 관리해야 합니다.
* 둘 이상의 클라우드와 해당 클라우드에서 실행되는 애플리케이션과 미들웨어를 관리하는 방법을 자동화해야 합니다.

## Todd와 Jane을 만나보세요
{: #vcscontent-modjourney-todd-jane}

Stock Trader 과정을 위해 Todd와 Jane에 초점을 맞춥니다. Todd는 ACME 회사의 운영 책임자이며 인프라, 보안, 클라우드 환경 및 여기서 실행되는 워크로드가
다양한 규정를 준수하도록 보증하는 정책에 대한 책임이 있습니다.

Jane은 Stock Trader 솔루션의 개발 책임자이며 Stock Trader 현대화를 책임지고 있습니다.
그녀는 기존 모놀리식 Stock Trader가 잘 실행되는 클라우드 기반 솔루션으로 현대화될 수 있도록 전체 개발 팀과 함께 개발 도구, 환경 및 플랫폼을 변경하는 작업을 수행합니다.

## Stock Trader를 만나보세요
{: #vcscontent-modjourney-meet-stock-trader}

Todd와 Jane은 WebSphere에서 실행되는 Stock Trader라는 애플리케이션을 빌드했습니다. Stock Trader에는 기본 사용자 인터페이스가 있지만 포트폴리오 관리자가 주식 매매와 내부 로열티 레벨 보기 등 포트폴리오를 관리하는 데 사용하는 신뢰할 수 있는 애플리케이션입니다.

Stock Trader는 WebSphere에서 실행되고, 몇 개의 .war 파일로 빌드되며, 수년 간 의존했던 데이터 센터에서 실행되는 전통적인 Db2 데이터베이스를 사용합니다. 인프라 팀, 개발 팀 및 데이터 팀 사이의 종속성 때문에 이 애플리케이션을 개선하는 데는 시간이 오래 걸립니다.

Stock Trader는 괜찮지만 회사의 모든 구성원은 보다 더 나은 것을 원하고 있습니다. 제품 관리자는 소셜 미디어를 로열티 프로그램에 추가하려고 합니다. Jane은 앱을 마이크로 서비스로 리팩토링할 수 있어서 기쁘게 생각합니다. 이를 통해 종속성이 줄어든 보다 강화된 기능을 계속해서 제공할 수 있습니다. Todd는 클라우드 효율성에 대한 아이디어를 좋아하지만, 회사 정책을 준수하도록 유지하기 위해서는 여전히 통제가 필요하다고 생각합니다.

## 과정을 위한 단계
{: #vcscontent-modjourney-steps}

Todd와 Jane은 솔루션을 현대화하기 위한 좋은 과정이 로드맵에서 시작한다는 것을 경험으로 알고 있습니다. 플랜을 변경할 수는 있지만 항상 비전을 통해 생각하고 그 곳에 도달할 실제적인 경로를 정의하는 것이 좋습니다. 각각의 단계는 회사에 가치를 가져다 주어야 하며 이러한 단계는 고객에게 비용이 드는 중단을 발생시킬 만큼 중요하지는 않습니다.

Todd와 Jane에게 Stock Trader 과정의 단계는 다음과 같습니다.
1. Stock Trader VM을 {{site.data.keyword.cloud_notm}}에 올립니다. 이 단계를 통해 Todd는 하드웨어와 로컬 데이터 센터에 있는 VMware 컨텐츠를 관리할 필요성을 줄일 수 있습니다.

2. WebSphere Application Server의 Stock Trader를 컨테이너의 Stock Trader로 변환합니다. Kubernetes에서 실행 중인 컨테이너가 오케스트레이션 및 기타 클라우드 동작을 일으키므로 이 단계를 회복성을 증가시킵니다. 이로 인해 Todd는 VMware vCenter Server on {{site.data.keyword.cloud_notm}} 환경에 {{site.data.keyword.cloud_notm}} Private 인스턴스를 준비한 다음 Jane과 함께 Transformation Advisor를 사용하여 Stock Trader를 컨테이너화해야 합니다.

3. 미들웨어를 {{site.data.keyword.cloud_notm}} Private에 리팩토링하고 추가합니다. 이 단계는 기존 미들웨어를 클라우드 환경으로 가져오고 클라우드 동작을 최적화합니다. 또한 라이센스 부여 과정을 간소화하고 다른
Kubernetes 환경에서도 사용할 수 있도록 완전히 이식 가능한 솔루션을 준비합니다.

4. Watson 및 기타 퍼블릭 클라우드 서비스를 강화합니다. 이 단계는 AI 서비스 및 전세계 클라우드 데이터 센터와 통신하는 기능을 끌어옴으로써 Stock Trader 환경에 잠재적으로 가치를 추가할 수 있습니다.

5. {{site.data.keyword.cloud_notm}} Kubernetes Service와의 진정한 하이브리드를 구현합니다. 이 단계를 통해 Todd는 관리 Kubernetes 서비스가 {{site.data.keyword.cloud_notm}} Private 인스턴스와 동일한 클라우드 지역에 계속해서 연결되도록 할 수 있습니다. 또한 Jane의 개발 팀은 핵심 {{site.data.keyword.cloud_notm}} Private 클러스터와 동일한 데이터 소스에 계속해서 액세스하는 동안에도 시험할 수 있는 개발 및 테스트 클러스터를 가질 수 있습니다.

6. DevOps를 현대화합니다. 이 과정을 통해 Jane은 Stock Trader를 제공하는 방법을 개선합니다.

7. 관리를 현대화합니다. Todd와 Jane은 Stock Trader를 관리하는 방법과 심지어 둘 이상의 클러스터와 클라우드 환경에서 Stock Trader가 실행되는 플랫폼을 관리하는 방법을 개선했습니다.

## 관련 링크
{: #vcscontent-modjourney-related}

* [vCenter Server on {{site.data.keyword.cloud_notm}} with Hybridity Bundle 개요](/docs/services/vmwaresolutions/archiref/vcs?topic=vmware-solutions-vcs-hybridity-intro)
