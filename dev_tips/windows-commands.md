---
title: "Windows 명령 프롬프트"
layout: post
date: 2026-11-06
author: pear27
tags: [Windows]
---

### 🔎 사용 중인 포트 찾기

```bash
netstat -ano # 사용 중인 포트 전체 조회
netstat -ano | findstr 3306 # 특정 포트 조회
```

---

### 🧹 프로세스 종료

위에서 찾은 PID를 사용하여 프로세스를 종료한다.

```bash
taskkill /f /pid <PID>
```

---
