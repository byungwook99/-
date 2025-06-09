# -# 🧠 리눅스 기반 보안 실습 포트폴리오 (사진 중심 정리)

## ✅ 웹 · 시스템 · 탐지 실습 사례 모음

---

### 🔗 1. PHP 웹 메뉴 구조 분석

![웹 메뉴 코드](php1.PNG)  
간단한 PHP 내비게이션 구성. 공격자는 이를 바탕으로 경로 예측 및 접근 제어 우회를 시도할 수 있음.

---

### 📊 2. PMM 서버 모니터링 구축

![PMM 서버 구축](pmm server 구축.PNG)  
Percona Monitoring & Management 설치 후 DB 상태, 쿼리 수, 연결 수 등 실시간 확인.

---

### 🔓 3. SetUID 이용 권한 상승

![SetUID root 획득](set uid를 이용한 일시적 root권한 획득.PNG)  
SetUID 바이너리를 이용하여 일반 계정에서 root 권한 일시 획득 성공.

---

### 💉 4. SQL Injection 실습

![SQLi 데이터 탈취](sql injection.PNG)  
sqlmap을 사용해 데이터베이스 내부 사용자 계정 및 로그 기록 탈취에 성공.

---

### 🛰️ 5. Suricata 로그 실시간 탐지

![Suricata 탐지 로그](suricata log.PNG)  
QUIC 프로토콜 디코딩 실패와 ICMP Ping 트래픽 탐지 로그 확인.

---

### 🌐 6. DNS 설정 실습

![DNS 구성](dns domain.PNG)  
내부 도메인에 대한 SOA 및 A 레코드 설정 결과.

---

### 🔥 7. Firewalld 포트 제어 설정

![방화벽 설정](firewall.PNG)  
특정 IP에서 HTTP만 허용하고 FTP는 차단하는 리치 룰 적용 예시.

---

### 📁 8. FTP 서버 접속 (FileZilla)

![FTP 연결](ftp 구축 파일질라 접속.PNG)  
192.168.5.122 서버 접속 후 파일 업로드 및 디렉터리 접근 테스트 수행.

---

### 📋 9. 시스템 로그 분석(LogAnalyzer)

![LogAnalyzer](log analyzer.PNG)  
syslog 메시지를 웹 기반으로 시각화하고, 이벤트 흐름을 확인함.

---

### 🐳 10. Docker 기반 보안 서비스 배포

![Docker 작동](도커 작동.PNG)  
PMM 서버 컨테이너가 정상 구동 중이며, 포트 바인딩 상태 확인 가능.

---

### 🛡️ 11. OSSEC 서버·클라이언트 구성

![OSSEC 구성](ossec server client.PNG)  
서버에 에이전트 등록 및 키 발급 상태. 각 시스템 이벤트 탐지 구조 구축 완료.

---

### 🌍 12. pfSense VPN 연동 확인

![pfSense VPN](pfsense.PNG)  
OpenVPN 클라이언트 연결 상태, IP 할당 여부 및 전송 바이트 확인.

---

### 🔎 13. Suricata 탐지 룰 커스터마이징

![Suricata 룰](suricata rules.PNG)  
ICMP Ping과 `/etc/passwd` 접근 시도를 탐지하기 위한 사용자 정의 룰 작성 예시.

---

### 📈 14. Zabbix 서버 및 클라이언트 구성

![Zabbix 연동](zabbix server client.PNG)  
Zabbix 서버와 클라이언트가 정상 연결되었고, 상태 및 데이터 수집 확인 가능.

---

### 🗃️ 15. MariaDB 데이터베이스 구축

![MariaDB](mariadb.PNG)  
`School` DB 생성 및 `Student_Score` 테이블을 활용한 쿼리 테스트 수행.

---

## 📎 관련 기술 키워드

- `Suricata`, `Snort`, `OSSEC`, `pfSense`, `Zabbix`, `Docker`, `MariaDB`
- `SQL Injection`, `File Upload`, `SetUID`, `Log Visualization`, `VPN 연동`

---

> 📌 이 포트폴리오는 직접 구축한 **보안 인프라 실습 환경**과 **공격/탐지 결과물**을 시각적으로 정리한 것입니다.
