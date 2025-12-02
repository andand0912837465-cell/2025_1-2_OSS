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
Week 10
1. OSS의 정의 및 의미

OSS(Open Source Software):
누구나 소스 코드를 자유롭게 보고(공개), 사용, 수정, 배포할 수 있는 라이선스를 만족하는 소프트웨어입니다.

핵심: 단순히 ‘무료’가 아니라 코드의 자유(Freedom) 보장이 목적입니다.

OSI(Open Source Initiative):
공개 소스 정의(OSD)를 관리하고 인증 마크를 부여하는 비영리 조직입니다.

자유 소프트웨어 vs 오픈소스:

자유 소프트웨어: 사용자 자유 강조(철학적)

오픈소스: 실용성과 기술 강조

2. OSS 주요 라이선스

GPL

Copyleft (강함)

소스 공개 의무 무조건

2차 저작물도 GPL 유지

LGPL

Copyleft (중간)

라이브러리 동적 링크 시 애플리케이션 공개 필요 없음

Apache License 2.0

Permissive (약함)

소스 공개 의무 없음

특허권 사용 허가 포함

MIT License

Permissive (가장 약함)

최소한의 조건(저작권 표시)만 준수

상업·수정·배포 자유

임시 저장(Stash) 개요

목적: 커밋하지 않은 변경 내용을 스택에 임시 저장하여 작업 디렉토리 비우기
영향: 작업 디렉토리 + 스테이징 영역 변경 모두 저장

Untracked 파일 삭제 (git clean)

git clean -n : 삭제될 파일 목록 미리 보기

git clean -f : 강제 삭제

git clean -i : 대화형 선택 삭제

Week 11
다양한 브랜치 병합

1) Fast-forward 병합

분기 후 메인 브랜치 변경 없음

병합 커밋 없이 포인터만 이동

2) 3-way 병합

양쪽 모두 커밋이 생겨 이력 분기 발생

공통 조상 기준으로 병합 커밋 생성

강제: git merge --no-ff

3) Squash 병합

서브 브랜치 커밋 여러 개 → 하나로 압축

명령: git merge --squash [브랜치명]

이후 사용자가 직접 git commit 실행

병합 충돌 처리

원인: 같은 파일 같은 라인 수정

표시 예시:

<<<<<<< HEAD
현재 브랜치 내용
=======
다른 브랜치 내용
>>>>>>> feature


해결 과정:

수정 & 마커 제거

git add

git commit

포기: git merge --abort

Week 12
브랜치 리베이스(Rebase)

목적: 히스토리를 일직선(Linear) 으로 만들기
명령:

git switch [서브]
git rebase [메인]


주의: 이미 원격에 공유된 커밋에는 금지
(동료의 이력 깨짐)

최신 커밋 수정 (--amend)
파일 수정 → git add → git commit --amend


가장 최근 커밋 덮어쓰기(새 커밋 ID)

과거 커밋 수정 (rebase -i)
git rebase -i HEAD~[개수]


주요 명령:

pick : 그대로

reword : 메시지만 변경

squash : 이전 커밋과 합치기

drop : 삭제

관련 도구

Source Control: 변경 상태 시각화

Git Graph: 시각적 이력

Diff: 변경 비교

Restore: 변경 취소 (git restore 기능)

Week 13
Reset (과거로 이동)

브랜치 포인터를 과거 커밋으로 이동 → 이후 이력 삭제 가능
git reset [커밋ID]

영향 범위에 따라:

Repository

Index

Working Directory
결과 달라짐

reset vs checkout

reset → 이력 삭제

checkout → 이력 보존, 과거 상태 확인

복구:

git reset --hard ORIG_HEAD

Revert (과거 취소 커밋 추가)

공유된 환경에서 안전한 되돌리기

원래 커밋은 보존됨

명령:

git revert [커밋ID]
git revert --no-edit


충돌 시:

해결 후: git revert --continue

포기: git revert --abort



