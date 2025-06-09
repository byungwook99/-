# 🔐 보안 실습 네트워크 구성도 요약

## 🗺️ 네트워크 아키텍처 개요

![보안 실습 토폴로지]gns3 topology.PNG

---

## 📌 구성 요소 요약

- **VLAN 분리**
  - VLAN 10: 서버
  - VLAN 20: 네트워크
  - VLAN 30: 보안 영역

- **침입 탐지 및 대응**
  - `Snort` – DDoS 및 `/etc/passwd` 접근 탐지
  - `Suricata` – curl, SQLi/XSS, ping 탐지 룰 작성
  - `OSSEC` – HIDS 기반 파일 무결성 및 에이전트 연동

- **방화벽 및 ACL 정책**
  - `ASA`와 `pfSense`를 통한 접근 제어
  - R3 ACL: 특정 IP에 대해서만 SSH/Ping 허용

- **CTF 실습 환경**
  - `DVWA`, `BoF`, `SetUID`, `StickyBit`, `wtmp` 로그 조작 실습
  - 주어진 Flag를 획득하고 로그를 분석하는 시나리오 기반 훈련

- **모니터링/시각화**
  - `Zabbix`, `LogAnalyzer`, `GoAccess`, `PMM` 도입
  - 웹 로그/시스템 로그 시각화 및 이상 탐지

- **VPN 구성**
  - `OpenVPN`을 통한 외부 원격 접속 실습 및 트래픽 라우팅

---

## 🎯 실습 목표

> 다양한 보안 장비와 실습 도구를 활용하여  
> **실제 공격 시나리오와 방어 대응을 체계적으로 학습**한 환경입니다.  
> 침입 탐지, 로그 분석, 권한 상승 실습 등 핵심 역량을 통합적으로 다뤘습니다
