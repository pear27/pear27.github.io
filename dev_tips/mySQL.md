---
title: "mySQL 사용법 정리"
layout: post
date: 2025-05-20
author: pear27
tags: [mySQL]
---

백엔드와 협업하며 MySQL 서버를 실행하고, 필요한 데이터를 직접 확인·테스트해야 할 때 빠르게 참고할 수 있는 실용적인 가이드입니다.  

---

### 🛠️ 1. MySQL 서버 실행하기 (Windows 기준)

1. **CMD 관리자 모드 실행**
   - `Win + R` → `cmd` 입력 → `Ctrl + Shift + Enter`

2. **MySQL 실행 및 로그인**
   ```bash
   net start mysql         
        # MySQL 서버 실행
   mysql -u root -p        
        # 사용자 로그인 (기본 사용자: root)
    ```

    * 이후 **비밀번호 입력** (개발자에게 공유받은 root 계정 비밀번호 사용)

3. **비밀번호가 기본값**(예: 0000)**일 경우 비밀번호 변경**

   ```bash
   ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'user123';
   FLUSH PRIVILEGES;
   ```

   * 위 명령은 `0000`으로 로그인한 후 `user123`으로 비밀번호를 변경하는 예입니다.

---

### 🧭 2. 데이터베이스 및 테이블 확인

```bash
SHOW DATABASES;           
    # 사용 가능한 데이터베이스 목록 확인
USE projectname;           
    # projectname 데이터베이스 선택
SHOW TABLES;              
    # 테이블 목록 보기
DESCRIBE user;            
    # user 테이블의 구조 확인
SELECT * FROM user;       
    # user 테이블 전체 데이터 조회
```

---

### 💡 프론트엔드 개발자를 위한 실전 팁

🔎 **데이터 빠르게 확인하기**

* 조건부 조회 (WHERE 문):

  ```sql
  SELECT * FROM user WHERE email = 'example@example.com';
  ```

* 특정 컬럼만 보기:

  ```sql
  SELECT id, username FROM user LIMIT 10;
  ```

* 최근 항목 정렬:

  ```sql
  SELECT * FROM post ORDER BY created_at DESC LIMIT 5;
  ```

🧪 **API 연동 전 DB 상태 확인**
* API 요청 전 후 `SELECT` 쿼리로 직접 확인하여 디버깅 가능
* REST API 응답이 이상하면, 실제 DB 값을 먼저 확인

---

### 📍 참고

* 관리자 권한으로 CMD를 실행해야 `net start mysql`이 정상 동작합니다.
* 로컬 DB와 원격 DB(운영/테스트 서버)를 혼동하지 않도록 주의하세요.

---

