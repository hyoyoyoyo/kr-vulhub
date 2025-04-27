# CVE-2012-2122 취약점 PoC 보고서

## 1. 개요
- CVE-2012-2122는 MySQL과 MariaDB 특정 버전에서 인증 우회가 가능한 취약점이다.
- memcmp 함수가 잘못된 캐스팅으로 -128~127 값을 반환하여, 1/256 확률로 인증을 우회할 수 있다.

## 2. 환경 구성 방법
- docker compose up -d 커맨드를 입력해 테스트 환경을 실행 (취약점이 보고된 MySQL 5.5.22의 컨테이너 이미지 사용)
- pymysql 패키지 설치

## 3. PoC 과정
- pip install pymysql로 패키지를 설치했다.
- python poc.py를 실행하여 인증 우회 공격을 수행하였다.
- 약 165번째 시도에서 root 계정 로그인에 성공하였다.

## 4. 취약점 분석
- 인증 메커니즘에서 잘못된 memcmp 결과로 인해 잘못된 패스워드도 1/256 확률로 승인된다.
- 공격자는 root 권한을 탈취할 수 있다.
- 

## 5. 실행과정

![image](https://github.com/user-attachments/assets/8fcbf85f-53d4-407b-97e8-3b4f3db68738)

![image](https://github.com/user-attachments/assets/960e6fe4-4861-4612-91ec-46b812485815)

![image](https://github.com/user-attachments/assets/88e83677-2693-4f5c-87c5-91f42c93dd56)
