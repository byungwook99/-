# 🔐 네트워크 & 리눅스 기반 보안 실습 환경 구성도

> 이 문서는 실제 보안 실습을 위해 구성한 네트워크와 리눅스 시스템 아키텍처를 시각적으로 표현하고,  
> 각 구성 요소에 대한 설명을 통해 실습 범위와 역량을 정리한 것입니다.

---

## 🗺️ 전체 토폴로지 구성도

[![보안 활동 토폴로지](gns3%20topology.PNG)](gns3%20topology.PNG)

---

## 🌐 네트워크 및 보안 정책 구성표

| 항목           | 구성 요소                 | 주요 설명 및 적용 내용                                      |
| -------------- | ------------------------- | ------------------------------------------------------------ |
| **VLAN 설계**  | VLAN 10                   | 서버 영역 (LogAnalyzer, FTP 등)                             |
|                | VLAN 20                   | 네트워크 영역 (테스트용 클라이언트)                         |
|                | VLAN 30                   | 보안 영역 (Zabbix, OSSEC 등)                                |
| **라우팅 구성**| R1 ~ R5                   | 정적 라우팅 설정, 구간별 통신 제어                         |
| **ACL 설정**   | R3                        | Kali 접근 허용, PC4→Firefox3 Ping 차단 등 세부 필터링       |
| **방화벽 (ASAv)** | Inside/DMZ/Outside 구분 | 구간별 HTTPS, Telnet, SSH 등 통제                          |
|                | DVWA → 내부 위치          | 외부 접근은 Telnet/HTTPS만 허용                             |
| **VPN 제어**   | pfSense                   | OpenVPN 서버 구성, 가상 외부 접속 환경 실습                 |


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

### 침투 및 취약점 공격 실습
- SQL Injection 및 Blind SQLi 공격을 통해 DB 탈취
- File Upload 우회 (php.kr, .phtml 등) 후 WebShell 업로드
- Reverse Shell 생성 및 권한 상승 (SetUID + Sticky Bit 조합)
- DVWA 플랫폼을 통한 OWASP Top 10 실습

### 침입 탐지 및 로그 분석
- Suricata: HTTP GET, XSS, SQLi, Reverse Shell 등 탐지 룰 작성
- OSSEC: File Integrity 검사 및 Rootkit 감지 실습

### 방화벽 및 접근 제어 테스트
- pfSense 기반 VPN 연동 실습 및 외부 접근 제한
- ASAv를 통한 DMZ/Inside/Outside 분리, Telnet/SSH 제한
- 라우터(R1~R5) ACL을 통한 Ping, SSH, HTTP 접근 통제

### 시스템 보안 환경 구성 및 유지
- 파일/폴더 권한 관리 실습 (`chmod`, `chown`, `setfacl` 등)
- `passwd` 정책 강화 (특수문자 포함, 최소 길이, 만료일 설정)
- DNS 내부 도메인 설정 및 서버 연동 실습

### 모니터링 및 자동화
- Zabbix: Agent 설치 및 로그 수집
- LogAnalyzer: 시스템 로그 통합 뷰 구성
- Docker 기반 PMM Server 구축 및 모니터링 확인
