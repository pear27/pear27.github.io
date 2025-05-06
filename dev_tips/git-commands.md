---
title: "Git 명령어 정리"
layout: post
date: 2025-05-06
author: pear27
tags: [github]
---

Git을 쓰다 보면 종종 실수를 하기도 하고, 명령어가 헷갈리는 경우가 있습니다. 이 글은 그런 상황을 빠르게 해결할 수 있도록 도와주는 **실전 중심 Git 명령어 모음**입니다.

---

### 🔄 가장 최근 커밋 되돌리기 (로컬)

```bash
git reset --soft HEAD~1
```

- 작업 내용과 staged 상태는 유지됩니다.

> ✅ `--soft`: 작업은 그대로, 커밋만 취소  
> ⚠️ `--hard`: 작업까지 실행 취소

---

### 🧹 가장 최근 커밋 되돌리기 (원격)

```bash
git checkout frontend   
    # 대상 브랜치(frontend)로 이동
git reset --hard HEAD~1 
    # 가장 최근 커밋을 삭제 (로컬)
git push origin frontend --force    
    # 강제로 원격에도 반영
```

- 협업 중이면 `--force` 대신 `--force-with-lease` 권장.

---

### 🧩 특정 커밋을 되돌리고 싶은 경우 (원격)

예: abcdef1 커밋이 문제라는 걸 알고 있을 때

**🔧 방법 1: git revert (이력 유지, 안전)**

```bash
git checkout frontend
git revert abcdef1
git push origin frontend
```

- 이력은 남기고, 실수는 되돌릴 수 있어 협업에 안전합니다.

> ♻️ `revert`: 해당 커밋의 반대 작업을 새 커밋으로 만들어 줍니다.

**🔧 방법 2: git reset --hard [commit-id 이전 커밋] + 강제 푸시**

```bash
git checkout frontend
git reset --hard 1234567
    # abcdef1 이전의 커밋으로 되돌림
git push origin frontend --force
```

- 원격까지 강제로 덮어쓰므로 주의가 필요합니다.

---

### 🧭 히스토리 확인

```bash
git log --oneline --graph --all
```

- 커밋 히스토리를 트리 형태로 한 줄씩 보기 좋게 출력
- 브랜치 흐름을 파악할 때 유용합니다.

---

### 🗑️ 로컬 변경사항 임시 저장 (stash)

```bash
git stash            # 현재 작업 저장 (임시 보관)
git stash pop        # 다시 꺼내서 적용
```

- 급히 다른 브랜치로 이동해야 할 때 사용
- 작업 내용이 사라지지 않아 안전

---