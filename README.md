# AWS EKS를 활용한 3Tier 웹서비스 구축

## 📑목차
- [프로젝트 소개](#-프로젝트-소개)
- [팀원 소개](#-팀원-소개)  
- [핵심 기술](#-핵심-기술)  
- [기술 스택](#-기술-스택)  
- [아키텍처](#-아키텍처)  
- [PAGE](#-page)  
- [테스트 영상](#-테스트-영상)  
- [산출물](#-산출물)

## 🖥️ 프로젝트 소개

본 프로젝트는 고객 친화적이고 효율적인 카페 서비스를 제공하기 위해 자가 서비스 방식의 주문 및 결제가 가능한 웹사이트를 구축하는 것을 목표로 합니다.

AWS의 관리형 서비스인 EKS를 활용하여 간편하면서도 안정적인 클라우드 인프라를 설계하였으며, CA와 HPA를 적용해 고가용성을 보장했습니다. JMeter 부하 테스트를 통해 시스템의 성능을 검증하였고, 이중화된 ALB를 구성하여 예기치 못한 상황에서도 안정적으로 서비스가 유지되도록 설계했습니다.

데이터 저장 및 접근 효율성을 위해 EFS를 도입하여 파일을 손쉽게 관리하고 확장할 수 있는 환경을 구축하였고 Redis를 활용한 Tomcat 세션 클러스터링과 고성능 인메모리 데이터 관리를 통해 빠르고 안정적인 데이터 처리를 구현했습니다. RDS와 Redis의 이중화 설정으로 데이터베이스의 안정성과 내구성을 강화했습니다.

서비스 할인 이벤트나 상품 정보 변경 시, ArgoCD와 GitHub를 연동한 CI/CD 파이프라인을 통해 업데이트를 자동화했습니다. 이를 통해 코드 변경 사항이 신속히 배포되며, 롤링 업데이트와 롤백 기능으로 안정적인 서비스 운영이 가능하도록 구성했습니다.

이러한 시스템 설계를 통해 안정적이고 효율적인 서비스 제공과 고객 만족도를 극대화할 수 있는 기반을 마련했습니다.



## 🙂 팀원 소개

| Name | 임희진 | 이재혁 | 이창수 | 장정원 |
| :------------: | :------------: | :------------: | :------------: | :------------: |
|  | ![임희진4](https://github.com/user-attachments/assets/685032f2-ef80-4e27-b0e4-b1e7c1de232b) | ![이재혁4](https://github.com/user-attachments/assets/ae5f9148-cb99-4322-8563-c120e89a7b8f) | ![황기창4](https://github.com/user-attachments/assets/7d7f190c-9ed3-4109-8361-b85141b9f88e) |
| __Position__ | Project Leader | Technology Leader| Engineer| Engineer|



## 🚀 핵심 기술
| Technology            | Description          |
|-----------------------|---------------------------------------------------------------------------------------------------|
| **EKS**         | Amazon EKS를 사용하여 Kubernetes 클러스터를 관리하고, AWS 인프라와 통합하여 자동화된 확장성과 고가용성 환경을 구축하였습니다. |
| **고가용성(HA)**         | CA, HPA, Multi-AZ, Read Replica, ALB 이중화를 통해 장애가 발생하더라도 서비스를 이용하는데 지장이 없도록 고가용성을 유지하였습니다. |
| **EFS**      | EFS를 사용하여 높은 가용성과 내구성을 보장하였습니다. 데이터 손실이나 장애 발생 시에도 안정적인 데이터 접근을 가능하게 하였습니다. |
| **Redis**    | 데이터를 메모리(RAM)에 저장하여 빠른 속도로 데이터에 접근할 수 있도록 하였습니다. 또한 사용자 세션 데이터를 저장하여, 여러 서버 간에 세션을 공유할 수 있으며, 빠르게 세션 데이터를 읽고 쓸 수 있도록 하였습니다. |
| **WAF** | WAF(Web Application Firewall)를 도입하여, SQL 인젝션, XSS 등 다양한 웹 공격으로부터 애플리케이션을 보호하고, 트래픽을 모니터링하여 악성 요청을 차단하는 보안 기능을 강화하였습니다. |
| **CI/CD** | GitHub와 ArgoCD를 연동하여 CI/CD 파이프라인을 구축하였습니다. 이로 인해 자동화 배포를 가능하게 하였습니다. |
| **모니터링**            | CloudWatch와 WhaTap을 연동하여 모니터링을 진행하였습니다. 클러스터에 장애 발생 시 경보 알림이 오도록 설정하였고 클러스터 내부를 시각화하여 직관적인 모니터링을 가능하게 하였습니다. |



## 🛠 기술 스택

<table>
<tr>
 <td align="center">프로그래밍 언어</td>
 <td>
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=JavaScript&logoColor=ffffff"/> <!--Java Script-->  
  <img src="https://img.shields.io/badge/Java-orange?style=for-the-badge&logo=Java&logoColor=white"/> <!--Java-->  
  <img src="https://img.shields.io/badge/html5-E34F26?style=for-the-badge&logo=html5&logoColor=white"/> <!--Html-->   
  <img src="https://img.shields.io/badge/css-1572B6?style=for-the-badge&logo=css3&logoColor=white"/> <!--Css-->  
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=MySQL&logoColor=white"/> <!--Sql-->  
 </td>
</tr>

<tr>
 <td align="center">프레임워크</td>
 <td>
  <img src="https://img.shields.io/badge/JSP-FF5F00?style=for-the-badge&logo=Java&logoColor=white"/> <!--Jsp-->  
  <img src="https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=Spring&logoColor=ffffff"/> <!--Spring-->  
 </td>
</tr>

<tr>
 <td align="center">인프라</td>
 <td>
  <img src="https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white"/> <!--AWS-->
  <img src="https://img.shields.io/badge/Kubernetes-326CE5?style=for-the-badge&logo=Kubernetes&logoColor=white"/> <!--Kubernetes-->  
  <img src="https://img.shields.io/badge/amazoneks-000000?style=for-the-badge&logo=amazoneks53&logoColor=#FF9900"/> <!--EKS-->
  <img src="https://img.shields.io/badge/Ubuntu-E95420?style=for-the-badge&logo=Ubuntu&logoColor=white"/> <!--Ubuntu-->
  <img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=ffffff"/> <!--Docker-->
  <img src="https://img.shields.io/badge/nginx-009639?style=for-the-badge&logo=nginx&logoColor=white"/> <!--Nginx-->
  <img src="https://img.shields.io/badge/tomcat-F8DC75?style=for-the-badge&logo=apachetomcat&logoColor=black"/> <!--Tomcat-->
  <img src="https://img.shields.io/badge/amazonrds-000000?style=for-the-badge&logo=amazonrds&logoColor=#527FFF"/> <!--RDS-->  
  <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=Redis&logoColor=white"/> <!--Redis-->  
  <img src="https://img.shields.io/badge/Amazon%20EC2-FF9900?style=for-the-badge&logo=Amazon%20EC2&logoColor=white"/> <!--EC2-->
  <img src="https://img.shields.io/badge/EFS-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="EFS"/> <!--EFS-->
  <img src="https://img.shields.io/badge/Amazon_ECR-FF4F00?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="ECR"/> <!--ECR-->
  <img src="https://img.shields.io/badge/linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"/> <!--Linux--> 
  <img src="https://img.shields.io/badge/MariaDB-003545?style=for-the-badge&logo=mariadb&logoColor=white"/> <!--MariaDB-->
  <img src="https://img.shields.io/badge/amazonroute53-000000?style=for-the-badge&logo=amazonroute53&logoColor=#8C4FFF"/> <!--Route53-->
  <img src="https://img.shields.io/badge/AWS%20ALB-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white"/> <!--ALB-->
  <img src="https://img.shields.io/badge/WAF-FF9900?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="WAF"/> <!--WAF-->
 </td>
</tr>

<tr>
 <td align="center">협업툴</td>
 <td>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white"/> <!--Git-->  
  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=GitHub&logoColor=white"/> <!--GitHub-->
 </td>
</tr>

<tr>
 <td align="center">기타</td>
 <td>
  <img src="https://img.shields.io/badge/Amazon_CloudWatch-2568B8?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="CloudWatch"/> <!--CloudWatch-->
  <img src="https://img.shields.io/badge/WhaTap-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhaTap"/> <!--WhaTap--> 
  <img src="https://img.shields.io/badge/Notion-000000?style=for-the-badge&logo=Notion&logoColor=white"/> <!--Notion-->  
  <img src="https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white"/> <!--Json-->  
 </td>
</tr>
</table>



## 🧱 아키텍처
![3차_3조전체시방서](https://github.com/user-attachments/assets/afa3839c-6442-4190-8153-7a8bcc13f981)



## 🌐 PAGE
* 메인
![main](https://github.com/user-attachments/assets/96d12c60-303f-43aa-878d-529cfa3af879)

* 회원가입
![signup](https://github.com/user-attachments/assets/71703698-b275-4023-8522-18d7b6ccf3a6)

* 로그인
![login](https://github.com/user-attachments/assets/9677e526-100e-4d74-b66b-da97f03ea029)

* 주문
![order1](https://github.com/user-attachments/assets/398a3a1b-84e2-44d7-9fac-27a0a931407d)
![order2](https://github.com/user-attachments/assets/38142566-6c7a-49b3-92e1-209ba20982f2)

* 예약
![reservation1](https://github.com/user-attachments/assets/611ceb9d-7467-4364-a23b-c77bd22181d9)

* 관리자 전용 페이지
![reservation2](https://github.com/user-attachments/assets/7ca37b6d-2539-4af0-8878-598bf6df85e9)

## 🧪 테스트 영상
* Redis 적용

![Redis](https://github.com/user-attachments/assets/e6cbeb7d-da8b-49da-b6d5-b97a80e2be3b)

* 롤링업데이트 및 롤백
  
![롤백](https://github.com/user-attachments/assets/254cafa6-b660-42e1-a24c-b1d705033493)

* 부하테스트 및 Whatap 모니터링

![부하테스트 및 Whatap 모니터링](https://github.com/user-attachments/assets/fa3cd54d-1fa3-499f-bafc-88482725109b)


## 📦 산출물
JSP는 용량문제로 코드만 첨부합니다.

PPT는 용량문제로 분할 첨부합니다.

* Terraform 소스코드
* Dockerfile
* yaml
* JSP
* WBS
* 관리대장
* 기술보고서
* PPT