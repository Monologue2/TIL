# Provisioning
> 사용자가 요청한 IT 자원을 사용할 수 있는 상태로 준비하는 것<br>
> 서버 자원, OS, 소프트웨어, 스토리지, 계정 프로비저닝 등이 있다. <br>
> 수동으로 처리하거나 자동화 툴을 이용해 자동으로 처리할 수 있다.

프로비저닝은 배포 단계의 초기 단계에 해당한다.<br>
프로비저닝과 구성 관리는 각기 다른 작업이지만, 둘 다 배포 프로세스의 단계에 포함된다.<br>
시스템을 프로비저닝 했으면, 다음 단계는 시스템을 구성하여 지속적으로 일관되게 유지 관리 하는 것이다.<br>

### 프로비저닝의 유형
####  서버 프로비저닝
물리 또는 가상 하드웨어를 설정하고, 운영 체제, 애플리케이션 같은 소프트웨어를 설치 및 구성하여 미들웨어, 네트워크, 스토리지 구성 요소에 연결하는 프로세스다.<br>
프로비저닝은 새로운 머신을 생성한 후 원하는 상태로 구현하는데 필요한 모든 운영을 포괄한다.<br>
[Ansible : 이벤트 기반 자동화로 서버 프로비저닝 자동화하기](https://youtu.be/Bt2tZB_5F2U)

#### 클라우드 프로비저닝
네트워크 요소 설치, 서비스 등과 같은 조직의 클라우드 환경에 맞는 기본 인프라를 생성하는 작업이 포함된다.<br>
기본 클라우드 인프라가 마련된 경우 프로비저닝에는 클라우드 내부의 리소스, 서비스, 애플리케이션을 설정하는 작업이 수반된다.<br>
[클라우드에 프로비저닝 자동화 적용하기](https://www.redhat.com/ko/engage/using-automation-public-cloud-detail)

#### 사용자 프로비저닝
사용자 프로비저닝은 이메일, 데이터베이스 또는 네트워큭와 같은 기업 환경 내부의 서비스와 애플리케이션에 권한을 부여하는 Identity 관리의 한 유형<br>
사용자 액세스를 취소하는 작업을 프로비저닝 해제라고 한다.<br>

사용자 프로비저닝의 한 가지 예는 [역할 기반 액세스 제어(RBAC)](https://www.redhat.com/ko/topics/security/what-is-role-based-access-control)이다.<br>
RBAC 구성에는 사용자 계정을 그룹에 할당하고 그룹의 역할을 정의하고 액세스 권한을 사용자의 요구에 따라 리소스에 부여하는 작업이 포함된다.<br>

#### 네트워크 프로비저닝
IT 인프라와 관련하여 네트워크 프로비저닝은 라우터, 스위치, 방화벽과 같은 구성 요소를 설치하고, IP 주소를 할당하고, 운영 상태 점검과 로그(팩트) 수집을 수행하는 것이다.<br>

통신사의 경우 전화번호 할당이나 장비 및 배선 설치와 같은 서비스를 사용자에게 제공하는 것을 말한다.

#### 서비스 프로비저닝
최종 사용자를 위한 IT 종속 서비스 설정 및 관련 데이터 관리가 포함된다.<br>
서비스로서의 소프트웨어(SaaS) 플랫폼에 대한 액세스 권한을 직원에게 부여하거나 자격 증명, 시스템 권한을 설정하여 특정 유형의 데이터 활동에 대한 액세스를 제한하는 작업을 들 수 있다.

### 자동화된 프로비저닝의 장점
프로비저닝을 위해 IT 팀이 새로운 애플리케이션을 배포하고 테스트하기 위해 VM에 대한 액세스 권한을 개발자에게 부여하는 등의 동일한 프로세스를 반복해야 하는 경우가 많다.<br>
리소스를 수동으로 프로비저닝 하는 경우 시간이 많이 소요되고 인적 오류가 발생하기 쉬워 새로운 제품과 서비스 출시가 지연될 수 있다.<br>

현재 대부분의 프로비저닝 Task는 코드형 인프라(IaC)로 자동화하여 처리할 수 있다.<br>
IaC에서는 인프라 사양이 구성 파일에 저장되므로 개발자는 스크립트를 실행하여 동일한 환경을 프로비저닝 할 수 있다.<br>

인프라를 코드화하면 IT팀이 프로비저닝을 위해 따라야 하는 템플릿이 제공된다.<br>
이 작업을 수동으로 처리할 수 있지만 자동화 툴을 사용하면 프로세스가 훨신 더 효율적으로 수행된다.

### 확인해야 할 사항
- 퍼블릭 및 프라이빗 클라우드, 네트워킹, 보안, 애플리케이션과 같은 활용 사례 지원 
- 여러 이기종 프로비저닝 툴의 작업을 가정하여 IT 비용 절감 
- IT 팀이 구성, Day 2 오퍼레이션, 오케스트레이션 프로세스를 관리할 수 있도록 지원
- 특정 명령을 제공하지 않고도 원하는 상태를 정의할 수 있는 선언적 구조 제공
- 보안 및 제어를 위한 셀프 서비스 및 역할 기반 액세스 기능 포함
- 독점 툴에 대한 벤더 종속성 제거

##### References
- [프로비저닝](https://www.redhat.com/ko/topics/automation/what-is-provisioning)
- [Speed up provisioning with Event-Driven Ansible (EDA)](https://youtu.be/Bt2tZB_5F2U)
- [Ansible, Kubespray 설명](https://waspro.tistory.com/558)
- [Ansible을 활용한 kubernetes 운영환경 구축하기](https://waspro.tistory.com/585)
- [Ansible](https://blog.naver.com/alice_k106/221333208746)