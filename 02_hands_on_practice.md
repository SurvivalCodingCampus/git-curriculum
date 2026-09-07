# [실습 워크북] 10단계 Git 손맛 챌린지 & 나만의 TIL 과제 제출

본 워크북은 오늘 배운 Git과 GitHub의 핵심 개념을 **가장 직관적인 10단계 손맛 실습**으로 완벽히 복습하고, **AI 시대에 남는 진짜 배움(TIL)을 작성하여 Pull Request(PR)로 제출**하는 실전 연습 가이드입니다.

---

## 🧭 실습 안내 및 사전 준비

- **소요 시간**: 약 30분 ~ 50분
- **실습 환경**: 터미널 (Windows PowerShell, macOS Terminal, Linux 등)
- **기본 원칙**:
  - 기본 브랜치는 **`master`**를 사용합니다.
  - 복사·붙여넣기보다 **직접 손으로 타이핑**하며 파일과 터미널의 변화를 관찰합니다.
  - "망가뜨려 봐야 복구할 수 있고, 지워봐야 깃허브의 가치를 깨닫습니다!"

---

## 🥊 PART 1. 10단계 Git & GitHub 손맛 챌린지

### STEP 1. 새로운 실습 저장소 만들기

홈 디렉터리(`~`) 아래 `dev/git_test2` 폴더를 만들고 Git 저장소로 초기화합니다.

```bash
# 1. 디렉터리 생성 및 이동
mkdir -p ~/dev/git_test2
cd ~/dev/git_test2

# 2. Git 저장소 초기화
git init
```

- **확인**: 터미널에 `Initialized empty Git repository in ...`이 표시되고 현재 브랜치가 `master`인지 확인합니다.

```bash
git status
# On branch master
# No commits yet
```

---

### STEP 2. 첫 번째 커밋 (`a.txt`)

> 💡 **실무 커밋 컨벤션 팁**:  
> 실무에서는 새로운 파일이나 기능을 추가할 때 주로 **`feat:`** 접두사를 붙입니다.  
> 이번 10단계 실습에서도 일관되게 `feat:` 접두사를 붙여 커밋해 봅시다!

`a.txt` 파일을 만들고 `aaa`라는 내용을 작성한 뒤 첫 번째 스냅샷(커밋)을 남깁니다.

```bash
# 1. 파일 생성 및 내용 입력
echo "aaa" > a.txt

# 2. 상태 확인 (책상 위 상태)
git status

# 3. 장바구니에 담기 (Staging)
git add a.txt

# 4. 금고에 영구 저장 (Commit)
git commit -m "feat: a.txt 파일 생성"
```

- **확인**: `git log`로 첫 번째 커밋 해시(알파벳+숫자)를 확인합니다.

```bash
git log --oneline
# a1b2c3d (HEAD -> master) feat: a.txt 파일 생성
```

---

### STEP 3. 두 번째 커밋 (`b.txt`)

새로운 파일 `b.txt`를 만들고 `bbb`를 적은 뒤 두 번째 커밋을 남깁니다.

```bash
# 1. b.txt 생성 및 입력
echo "bbb" > b.txt

# 2. 스테이징 및 커밋
git add b.txt
git commit -m "feat: b.txt 파일 생성"
```

- **확인**: 커밋이 2개로 늘어났는지 확인합니다.

```bash
git log --oneline
# e4f5g6h (HEAD -> master) feat: b.txt 파일 생성
# a1b2c3d feat: a.txt 파일 생성
```

---

### STEP 4. 세 번째 커밋 (기존 파일 `a.txt` 수정)

기존에 있던 `a.txt` 파일에 `ccc`라는 내용을 덧붙이고 세 번째 커밋을 남깁니다.

```bash
# 1. a.txt 파일에 ccc 덧붙이기 (>> 사용)
echo "ccc" >> a.txt

# 2. 무엇이 바뀌었는지 눈으로 확인
git diff

# 3. 스테이징 및 커밋
git add a.txt
git commit -m "feat: a.txt 내용 추가"
```

- **확인**: 커밋이 총 3개가 되었습니다!

```bash
git log --oneline
# 7i8j9k0 (HEAD -> master) feat: a.txt 내용 추가
# e4f5g6h feat: b.txt 파일 생성
# a1b2c3d feat: a.txt 파일 생성
```

---

### STEP 5. GitHub 원격 저장소에 푸시(Push)하기

지금까지 로컬 컴퓨터 금고에 저장한 3개의 커밋을 클라우드 금고(GitHub)에 안전하게 백업합니다.

1. **GitHub 웹사이트 접속** $\rightarrow$ 우측 상단 `+` 버튼 클릭 $\rightarrow$ **New repository** 선택
2. **Repository name**: `git_test2` 입력
3. **Public** 선택 (README, .gitignore 체크박스는 **모두 해제**한 채로 `Create repository` 클릭)
4. 생성된 화면의 안내에 따라 로컬 터미널에서 다음 명령어 실행:

```bash
# 1. 원격 저장소 주소 등록
git remote add origin https://github.com/<본인-GitHub-아이디>/git_test2.git

# 2. master 브랜치 푸시
git push -u origin master
```

- **확인**: 브라우저에서 GitHub 저장소 페이지를 새로고침(F5)합니다. `a.txt`와 `b.txt`, 그리고 3개의 커밋이 올라와 있는지 확인합니다.

---

### STEP 6. ⚡ 처음 커밋으로 Hard Reset 돌리기 (타임머신!)

과거로 되돌아가는 강력한 타임머신 명령어를 실행해 봅니다.

먼저 첫 번째 커밋의 해시(예: `a1b2c3d`)를 확인합니다.

```bash
git log --oneline
# 7i8j9k0 (HEAD -> master, origin/master) feat: a.txt 내용 추가
# e4f5g6h feat: b.txt 파일 생성
# a1b2c3d feat: a.txt 파일 생성  <-- 이 첫 커밋으로 되돌릴 것입니다!
```

이제 첫 커밋으로 강제로 되돌립니다:

```bash
git reset --hard <첫_커밋_해시>
# 예시: git reset --hard a1b2c3d
# 출력: HEAD is now at a1b2c3d feat: a.txt 파일 생성
```

> [!CAUTION]
> #### 💡 잠깐! 터미널을 확인하기 전에 머릿속으로 먼저 예측해 보세요!
> 1. **Q1. 지금 폴더 안에 `b.txt` 파일은 남아있을까요, 아니면 사라졌을까요?**
> 2. **Q2. `a.txt` 파일을 열면 내용이 `aaa`만 있을까요, 아니면 `ccc`도 남아있을까요?**

직접 확인해 봅시다!

```bash
# 1. 현재 폴더 파일 목록 확인
ls

# 2. a.txt 내용 확인
cat a.txt

# 3. 커밋 히스토리 확인
git log --oneline
```

- **결과 확인**:
  - `b.txt`는 감쪽같이 사라졌습니다! (두 번째 커밋에서 만들었으므로 첫 커밋에는 존재하지 않음)
  - `a.txt`의 내용은 오직 `aaa`만 남아있습니다!
  - `git log`를 쳐봐도 방금 전까지 있던 2개 커밋이 사라지고 오직 첫 커밋만 보입니다.

---

### STEP 7. 🛡️ 원격 저장소(GitHub)의 내용으로 완벽 복구하기

"망했다! 내 코드와 커밋이 다 날아갔다!"라고 당황할 필요가 없습니다.  
우리는 **STEP 5에서 GitHub에 이미 push를 해두었기 때문**입니다!

클라우드 금고(GitHub)에 백업해 둔 최신 상태로 로컬을 다시 되돌립니다.

```bash
# GitHub 원격의 최신 master 상태로 강제 복구
git reset --hard origin/master
```

- **확인**:
  - `ls`를 쳐보면 사라졌던 `b.txt`가 마법처럼 돌아와 있습니다!
  - `cat a.txt`를 쳐보면 `ccc` 내용까지 완벽하게 복구되었습니다!
  - `git log --oneline`을 쳐보면 3개의 커밋이 모두 원래대로 살아있습니다.

> **💡 핵심 깨달음**: "로컬에서 아무리 큰 실수를 저질러도, 원격에 push된 기록이 있다면 언제든 완벽하게 복구할 수 있다!"

---

### STEP 8. 💥 폴더를 통째로 삭제해버리기 (극단적 상황 연출)

이번엔 아예 로컬 폴더 자체를 통째로 지워버리는 가상의 재난 상황을 만들어 봅니다.

```bash
# 1. 상위 폴더로 빠져나오기
cd ~/dev

# 2. 실습 폴더 통째로 강제 삭제!
rm -rf git_test2
```

- **확인**: `ls`를 해보면 `git_test2` 폴더가 완전히 사라졌습니다. 로컬 컴퓨터에서는 더 이상 파일의 흔적조차 찾을 수 없습니다.

---

### STEP 9. 🌟 Clone으로 기적의 부활 (새 폴더 `git_test3`)

내 컴퓨터가 고장 났거나 폴더가 삭제되어도, GitHub에 저장소가 있다면 새로운 폴더로 언제든 복원할 수 있습니다.

```bash
# 원격 저장소를 git_test3라는 새 폴더로 복제(Clone)
git clone https://github.com/<본인-GitHub-아이디>/git_test2.git git_test3

# 복제된 폴더로 이동
cd git_test3
```

- **확인**:
  - `ls`로 `a.txt`, `b.txt`가 그대로 살아있는지 확인합니다.
  - `git log --oneline`으로 3개의 커밋 기록이 온전히 보존되어 있는지 확인합니다.

---

### STEP 10. 새로운 작업 및 다시 푸시 (`d.txt`)

부활한 새 작업 공간에서도 평소처럼 파일 작업을 이어갈 수 있음을 확인합니다.

```bash
# 1. d.txt 생성 및 내용 작성
echo "ddd" > d.txt

# 2. 커밋
git add d.txt
git commit -m "feat: d.txt 파일 생성"

# 3. GitHub 원격으로 푸시
git push origin master
```

- **확인**: 브라우저에서 GitHub 저장소 페이지를 새로고침하여 `d.txt`가 성공적으로 등록되었는지 확인합니다!

---

## 📝 PART 2. Day 1 최종 미션: AI 시대를 이기는 진짜 배움, 나만의 TIL 과제

> [!IMPORTANT]
> ### 💡 AI 시대의 과제 작성 철학
> 인공지능에게 "오늘 배운 Git 요약해 줘"라고 시켜서 나오는 텍스트를 복사·붙여넣기 하는 것은 학습자 본인의 성장에 아무런 도움이 되지 않습니다.
> 
> 오늘 과제는 **내가 직접 겪은 손맛, 실수했던 순간, 그리고 헷갈렸던 용어를 '나만의 언어'로 재해석**하여 작성합니다.  
> 초등학생 동생이나 비전공자 친구에게 말하듯이 쉽고 명쾌한 비유를 곁들여 작성해 보세요!

---

### 1. 과제 파일 작성 템플릿 (`assignments/day01/이름.md`)

> **역할**: 내 깃허브에 평생 남길 **순수 기술 & 개념 자산**입니다.  
> 아래 양식을 복사하여 `assignments/day01/본인이름.md` 파일에 채워 넣습니다.

```markdown
# [TIL] Day 01 - Git & GitHub 첫걸음

- **작성자**: 홍길동
- **작성일**: 2026-09-06

---

## 1. 오늘 내가 직접 손으로 치며 배운 점
- (강의를 들으며 터미널에 직접 타이핑하고 관찰한 기술적 동작과 명령어)

## 2. 가장 멘붕이었던 순간 & 트러블슈팅
- **문제 상황**: (예: `reset --hard`로 파일이 사라졌을 때, 푸시 인증 오류 등)
- **원인 및 해결 과정**: 

## 3. 나만의 언어로 재해석한 핵심 용어 사전
> 💡 사전식 정의나 AI 복붙 금지! 초등학생 동생이나 비전공자 친구에게 설명하듯 "나만의 비유"로 작성:
- **Git**: (예: 코드의 타임머신 세이브 파일 관리기)
- **Commit**: (예: 게임 보스전 직전 남겨두는 1개의 완벽한 세이브 슬롯)
- **Staging Area**: (예: 마트에서 계산대에 올리기 전, 장바구니에 담아둔 상태)
- **Remote (원격 저장소)**: (예: 내 컴퓨터가 벼락 맞아 터져도 안전하게 보관되는 클라우드 금고)
- **Branch**: (예: 원본을 건드리지 않고 마음껏 실험해볼 수 있는 나만의 평행세계)
- **Pull Request (PR)**: (예: "선생님, 제가 작업한 코드 검토하시고 본사 메인 금고에 합쳐주세요!"라고 보내는 공식 편지)
```

---

### 2. 과제 제출 규정 (엄격 준수)

선생님이 공유해 주신 **공용 과제 저장소**에 Pull Request(PR)로 제출합니다.

| 구분 | 규칙 | 예시 |
| :--- | :--- | :--- |
| **과제 저장 위치** | `assignments/day01/이름.md` | `assignments/day01/홍길동.md` |
| **작업 브랜치명** | `submit/이름-day01` | `submit/홍길동-day01` |
| **PR 제목 형식** | **`01_이름_Git버전관리`** | **`01_홍길동_Git버전관리`** |

---

### 3. Step-by-Step 과제 제출 절차

#### ① 원본 과제 저장소 Fork
선생님의 과제 저장소(예: `https://github.com/teachers-repo/git-assignments`)에 접속한 뒤, 우측 상단의 **`Fork`** 버튼을 눌러 내 GitHub 계정으로 복제합니다.

#### ② 내 로컬 컴퓨터로 Clone
내 계정으로 Fork된 저장소를 내 컴퓨터로 가져옵니다.

```bash
cd ~/dev
git clone https://github.com/<내-GitHub-아이디>/git-assignments.git
cd git-assignments
```

#### ③ 제출용 브랜치 생성 및 이동
반드시 본인 이름이 들어간 브랜치를 새로 만들어 작업합니다.

```bash
git switch -c submit/홍길동-day01
```

#### ④ 과제 파일 작성 및 커밋
`assignments/day01/` 폴더 아래 본인 이름으로 마크다운 파일을 작성합니다.

```bash
# 폴더 확인 (없으면 생성)
mkdir -p assignments/day01

# 파일 작성 (VS Code 등 에디터로 열어서 템플릿 채우기)
code assignments/day01/홍길동.md
```

작성이 끝났으면 커밋합니다:

```bash
git add assignments/day01/홍길동.md
git commit -m "feat: 홍길동 Day 01 TIL 과제 작성"
```

#### ⑤ 내 원격 저장소로 Push
작성한 브랜치를 내 GitHub 원격 저장소로 올립니다:

```bash
git push -u origin submit/홍길동-day01
```

#### ⑥ GitHub 웹에서 Pull Request(PR) 생성 및 본문 작성
1. 내 GitHub 저장소 페이지 상단에 나타난 **`Compare & pull request`** 초록색 버튼을 클릭합니다.
2. **Base repository**: `선생님-저장소 (master)` $\leftarrow$ **Head repository**: `내-저장소 (submit/홍길동-day01)` 확인
3. **PR 제목**을 규칙에 맞춰 정확히 작성합니다:
   ```text
   01_홍길동_Git버전관리
   ```
4. **PR 본문(Description) 작성**:  
선생님이 PR을 열자마자 핵심 이해도와 회고를 한눈에 보실 수 있도록 아래 템플릿을 본문 창에 작성합니다:

```markdown
## 📌 오늘의 핵심 3줄 요약
1. 
2. 
3. 

---

## 💭 오늘 하루 회고 (KPT)
- **Keep (오늘 실습하며 앞으로도 유지하고 싶은 좋은 습관)**: 
- **Problem (오늘 실습 중 아쉬웠거나 헤맸던 점)**: 
- **Try (내일 수업이나 실습에서 새롭게 시도해볼 점)**: 

---

## 💬 선생님께 질문 & 한마디
- 
```

5. 초록색 **`Create pull request`**를 클릭하여 제출을 완료합니다!

---

## 🎉 축하합니다!
- 이제 여러분은 Git의 3대 영역, 안전한 되돌리기, 원격 저장소 백업과 복구, 그리고 실무 협업의 핵심인 **Pull Request 제출**까지 모든 과정을 완벽히 마쳤습니다!
- 선생님의 코드 리뷰와 Merge를 기다려 보세요!
