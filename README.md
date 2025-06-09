# 🔐 네트워크 & 리눅스 기반 보안 실습 환경 구성도

> 이 문서는 실제 보안 실습을 위해 구성한 네트워크와 리눅스 시스템 아키텍처를 시각적으로 표현하고,  
> 각 구성 요소에 대한 설명을 통해 실습 범위와 역량을 정리한 것입니다.

---

## 🗺️ 전체 토폴로지 구성도

[![보안 활동 토폴로지](gns3%20topology.PNG)](gns3%20topology.PNG)

---

## 🌐 네트워크 구성 개요

- **VLAN 분할 및 계층 구조 설계**
  - VLAN 10: 서버 (Server Zone)
  - VLAN 20: 네트워크 장비 (Network Zone)
  - VLAN 30: 보안 장비 (Security Zone)

- **라우팅 및 인터라우터 통신**
  - R1~R5 간 정적 라우팅 구성
  - 내부 네트워크 세분화 및 흐름 제어 가능

- **ACL (Access Control List) 설정**
  - R3: 특정 호스트에서 Kali 접근 허용
  - PC4 → Firefox3 Ping 차단 등 세부 제어 시나리오 구현
  - 불필요한 트래픽 차단을 통한 최소 권한 원칙 적용

- **ASAv (Adaptive Security Appliance) 방화벽**
  - Inside/DMZ/Outside 영역 분리
  - DVWA 서버는 Inside 영역에 위치하며, 외부 접근은 https/telnet만 허용
  - 서버와 내부 호스트 간 SSH, DNS 제어 적용

- **pfSense 기반 VPN 설정**
  - Remote-Access를 위한 OpenVPN 구성
  - 가상사설망을 통한 외부 사용자 접근 테스트 가능

---

## 🧱 주요 Linux 시스템 설명

| 시스템 역할 | OS 버전 | 주요 기능 및 용도 |
|-------------|---------|------------------|
| **Kali** | Kali Linux | 공격자 역할, CTF 공격 시나리오 수행, SQLi/Reverse Shell 등 실습 |
| **DVWA/CTF 서버** | Rocky Linux | DVWA 기반 공격 대상, Flag 수집 및 취약점 실습 대상 |
| **LogAnalyzer/웹 서버** | Rocky Linux | Suricata, OSSEC 로그 수집 및 분석 웹 서버 |
| **FTP 서버** | Rocky Linux | 취약한 설정이 있는 FTP 서버, 파일 업로드 실습 |
| **Zabbix 서버** | Rocky Linux | 모니터링 서버, 에이전트 정보 수집 |
| **DNS 서버** | Rocky Linux | 내부 도메인 설정 및 테스트 용도 |
| **OSSEC 서버/에이전트** | Rocky Linux | HIDS 탐지용. 서버-클라이언트 구조로 로그 무결성 실습 |
| **pfSense** | pfSense | VPN 및 방화벽 실습. OpenVPN 터널링 테스트 |
| **Snort 서버** | Rocky Linux | ICMP, DDoS, /etc/passwd 접근 탐지 등 시그니처 기반 NIDS |

---

## 🔍 실습 포인트

### 🔸 침투 및 취약점 공격 실습

- SQL Injection 및 Blind SQLi 공격을 통해 DB 탈취
- File Upload 우회 (php.kr, .phtml 등) 후 WebShell 업로드
- Reverse Shell 생성 및 권한 상승 (SetUID + Sticky Bit 조합)
- DVWA 플랫폼을 통한 OWASP Top 10 실습

### 🔸 침입 탐지 및 로그 분석

- Suricata: HTTP GET, XSS, SQLi, Reverse Shell 등 탐지 룰 작성
- OSSEC: File Integrity 검사 및 Rootkit 감지 실습

### 🔸 방화벽 및 접근 제어 테스트

- pfSense 기반 VPN 연동 실습 및 외부 접근 제한
- ASAv를 통한 DMZ/Inside/Outside 분리, Telnet/SSH 제한
- 라우터(R1~R5) ACL을 통한 Ping, SSH, HTTP 접근 통제

### 🔸 시스템 보안 환경 구성 및 유지

- 파일/폴더 권한 관리 실습 (`chmod`, `chown`, `setfacl` 등)
- `passwd` 정책 강화 (특수문자 포함, 최소 길이, 만료일 설정)
- DNS 내부 도메인 설정 및 서버 연동 실습

### 🔸 모니터링 및 자동화

- Zabbix: Agent 설치 및 로그 수집
- LogAnalyzer: 시스템 로그 통합 뷰 구성
- Docker 기반 PMM Server 구축 및 모니터링 확인
