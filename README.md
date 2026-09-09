# 🚀 Git & GitHub 실전 핸즈온 (Day 1)

> **과정명**: 비전공자/주니어 개발자를 위한 Git & GitHub 시작부터 PR 과제 제출까지  
> 생존코딩 오준석  
> **진행 방식**: 설명 20% + 실습 80%의 **따라하기(Google Codelab/Hands-on)** 방식  
> **최종 목표**: 로컬 버전 관리 기초를 완벽히 이해하고, GitHub에서 **Pull Request(PR)로 과제를 제출**할 수 있다.

---

## 🧭 커리큘럼 구성 (Day 1)

| 단계 | 모듈명 | 주요 학습 및 실습 내용 |
| :---: | :--- | :--- |
| **0단계** | **[환경 준비 & Git 첫걸음](./01_git_hands_on_day1.md#0단계-환경-준비--git-첫걸음-설치와-초기-설정)** | • Git이란 무엇인가? 왜 쓰는가?<br>• Windows(`winget`), macOS(`brew`) 설치<br>• PowerShell vs Git Bash vs **WSL2 장기적 권장 비교**<br>• 필수 전역 설정(`user.name`, `user.email`, `autocrlf` 등) |
| **1단계** | **[Git 3대 영역과 로컬 버전 관리](./01_git_hands_on_day1.md#1단계-git의-3대-영역과-로컬-버전-관리-기본-커맨드)** | • Git 3가지 공간: 작업 디렉터리 $\rightarrow$ 스테이징 영역 $\rightarrow$ 저장소<br>• `git init`, `git status`<br>• `git add .`, `git commit -m "..."`<br>• `git log --oneline --graph`<br>• `.gitignore` 실습 |
| **2단계** | **[변경 사항 비교와 안전하게 되돌리기](./01_git_hands_on_day1.md#2단계-변경-사항-비교와-안전하게-되돌리기-undo--checkout-비교)** | • `git diff` 및 `git diff --staged`<br>• 최신 `git restore`로 파일 수정 취소 (🔍 `git checkout --` 비교)<br>• 최신 `git restore --staged`로 언스테이징 (🔍 `git reset HEAD` 비교)<br>• 직전 커밋 수정: `git commit --amend` |
| **3단계** | **[GitHub 원격 저장소 연동과 동기화](./01_git_hands_on_day1.md#3단계-github-원격-저장소remote-연동과-동기화)** | • 로컬 저장소와 원격 저장소(GitHub)의 개념<br>• GitHub 리포지토리 생성 및 연결 (`git remote add origin`)<br>• 첫 푸시 (`git push -u origin master`)<br>• 복제(`git clone`) 및 동기화(`git pull`) 실습 (1인 2역) |
| **4단계** | **[브랜치(Branch) 기초와 평화로운 병합](./01_git_hands_on_day1.md#4단계-브랜치branch-기초와-평화로운-병합-merge)** | • 브랜치의 개념과 독립적 작업 환경<br>• 최신 `git switch -c` 브랜치 생성 및 이동 (🔍 `git checkout -b` 비교)<br>• 기능 구현 및 커밋<br>• Fast-Forward 로컬 병합 (`git merge`)<br>• 브랜치 삭제 (`git branch -d`) |
| **5단계** | **[협업의 꽃! Pull Request(PR)로 과제 제출](./01_git_hands_on_day1.md#5단계-협업의-꽃-pull-requestpr로-과제-제출하기-최종-미션)** | • 왜 main에 직접 푸시하지 않고 PR을 쓰는가?<br>• 과제 저장소 Fork $\rightarrow$ Clone $\rightarrow$ 브랜치 분기<br>• 과제 작성(자기소개 프로필) 후 커밋 & 푸시<br>• GitHub PR 생성, 코드 리뷰 코멘트 작성, 머지 확인<br>• Day 1 정리 & Day 2(찐 협업: 충돌 해결, Rebase) 예고 |

---

## 📌 Day 1의 범위 원칙

1. **"첫날은 과제 제출(PR)까지 막힘없이 성공하는 것이 핵심!"**
   - 수강생들이 첫날 Git에 질리지 않고, "버전 관리의 흐름과 협업 방식(PR)"을 온전히 체득하는 데 집중합니다.
2. **복잡한 브랜치 충돌(Conflict) 해결과 심화 커맨드는 별도 분리**
   - 별도 수업에서 진행   

---

## 💻 실습 교안 & 워크북 바로가기

1. 📖 **[Day 1 메인 이론 및 실습 교안 (01_git_hands_on_day1.md)](./01_git_hands_on_day1.md)**
   - 0단계(설치)부터 5단계(PR 과제)까지 개념과 실습을 완벽히 다루는 올인원 가이드
2. 🥊 **[10단계 손맛 챌린지 & 나만의 TIL 과제 워크북 (02_hands_on_practice.md)](./02_hands_on_practice.md)**
   - 군더더기 없는 10단계 핵심 손맛 실습 (로컬 생성 $\rightarrow$ 3회 커밋 $\rightarrow$ 원격 푸시 $\rightarrow$ hard reset 예측 퀴즈 $\rightarrow$ 원격 복구 $\rightarrow$ 폴더 삭제 $\rightarrow$ clone 부활)
   - AI 시대를 이기는 나만의 언어로 작성하는 TIL 과제 작성 및 PR 제출 가이드 (`01_이름_Git버전관리`)
3. ☕ **[Day 2 Java 기초 핸즈온 교안 (03_java_basics_hands_on.md)](./03_java_basics_hands_on.md)**
   - 코딩 무경험자/창업자를 위한 4시간 완성 Java 기초 (변수, 조건문, 반복문, 메서드 5대 기둥 실습)
   - IntelliJ 단일 통합 설치, 2인 1조 페어 코드 워크스루, assignments/day02/ 과제 제출 가이드

