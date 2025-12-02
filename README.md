# 2025_1-2_OSS
1학년 2학기 오픈소프트웨어과목 저장소

##  Week 1
##  Week 2
##  Week 3
##  Week 4
##  Week 5
##  Week 6
##  Week 7
##  Week 8
##  Week 9
# Week 10

## 1. OSS의 정의 및 의미
- **OSS(Open Source Software)**  
  누구나 소스 코드를 자유롭게 보고, 사용, 수정, 배포할 수 있는 소프트웨어
- 핵심: 단순한 무료가 아니라 **자유(Freedom) 보장**
- **OSI(Open Source Initiative)**  
  공개 소스 정의(OSD) 관리 및 인증 마크 부여
- **자유 소프트웨어 vs 오픈소스**
  - 자유 소프트웨어: 사용자의 자유, 철학 강조
  - 오픈소스: 실용성, 기술적 활용 강조

## 2. OSS 주요 라이선스
- **GPL**
  - Copyleft 강함
  - 소스 공개 의무 O
  - 파생물도 반드시 GPL 유지
- **LGPL**
  - Copyleft 중간
  - 동적 링크 시 애플리케이션 공개 X
- **Apache 2.0**
  - Permissive 약함
  - 소스 공개 의무 X
  - 특허 사용 허용
- **MIT**
  - Permissive 매우 약함
  - 저작권 명시만 하면 자유로움

## 3. Stash (임시 저장)
- 커밋하지 않은 변경 사항을 스택에 저장
- 브랜치 전환 시 임시 보관에 사용

## 4. Untracked 파일 삭제
```bash
git clean -n   # 삭제될 목록 확인
git clean -f   # 실제 삭제
git clean -i   # 대화형 선택 삭제
````

---

# Week 11 — Merge

## 1. Fast-forward Merge

* 이력이 일직선일 때
* 병합 커밋 없이 포인터만 이동

## 2. 3-way Merge

* 이력이 갈라진 상황
* 공통 조상 기준으로 병합 커밋 생성

```bash
git merge --no-ff [branch]  # 강제로 병합 커밋 생성
```

## 3. Squash Merge

* 여러 커밋을 하나로 압축

```bash
git merge --squash [branch]
git commit
```

## 4. 병합 충돌

* 동일 라인을 다르게 수정한 경우
* 메시지: `CONFLICT (content)`

## 5. 충돌 해결

* 마커 제거 후 스테이징

```bash
git add [file]
git commit
git merge --abort   # 충돌 해결 취소 시
```

---

# Week 12 — Rebase

## 1. Rebase 개요

* 커밋 기준점을 다른 커밋 위로 이동
* 히스토리를 **직선(Linear)** 으로 유지

## 2. 주의사항

* **공유된 커밋에는 절대 사용 금지**

## 3. 최신 커밋 수정

```bash
git add [file]
git commit --amend
```

## 4. 과거 커밋 수정 (Interactive Rebase)

```bash
git rebase -i HEAD~N
```

* pick: 그대로
* reword : 메시지 수정
* squash: 이전 커밋과 통합
* drop: 삭제

## 5. VS Code 기능

* Source Control 메뉴
* Git Graph 확장
* Diff 비교
* Restore로 변경 취소

---

# Week 13 — 버전 되돌리기

## 1. Reset 개요

* 브랜치 포인터 이동 → **이력 삭제 위험**
* Repository / Index / Working Directory 각각에 영향 다름

```bash
git reset --hard ORIG_HEAD  # 실수 복구 가능
```

## 2. Revert 개요

* 원격 공유 커밋 되돌릴 때 안전
* 새로운 취소 커밋 추가

```bash
git revert [commitID]
git revert --no-edit
git revert --continue
git revert --abort
```

```

---

이제 Git에서 줄바꿈도 완벽하게 보입니다.  
원하면 제목 색상, 그림, 커밋 그래프 시각화도 추가해 드릴 수 있어요.  
또 GitHub README 스타일로 아이콘 달아서 더 예쁘게 꾸밀 수도 있고요.
```




