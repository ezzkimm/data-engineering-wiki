# README Wiki Structure Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 루트 README로 학습 기록을 탐색하고 모든 회고를 `review` 폴더에서 주차별로 찾을 수 있게 한다.

**Architecture:** 회고 원문을 `review/daily/weekN`과 `review/weekly`로 이동한다. 루트 README는 문서형 인덱스이고, 각 일일 회고 주차 폴더에는 날짜순 링크를 제공하는 `README.md`를 둔다.

**Tech Stack:** GitHub Flavored Markdown, Git

**Spec:** `docs/superpowers/specs/2026-08-31-readme-wiki-structure-design.md`

## Global Constraints

- 최종 학습 문서 구조는 루트 `README.md`와 `review/`만 사용한다.
- 일일 회고의 Week 1은 2026-07-01~03, 이후 주차는 월요일~일요일이고 2026-08-31은 Week 10이다.
- 기존 회고 원문은 바꾸지 않는다.
- README와 모든 인덱스의 상대 링크 대상은 저장소 안에 존재해야 한다.

---

### Task 1: 회고 문서 이동

**Files:**
- Move: 루트의 날짜별 `*.md` → `review/daily/week1`~`week10/`
- Move: `week1.md`~`week6.md`, `project.md` → `review/weekly/`
- Delete: `Home.md`

**Interfaces:**
- Consumes: 루트에 있는 46개 일일 회고, 6개 주차 회고, 프로젝트 회고
- Produces: `review/daily/weekN/` 및 `review/weekly/`의 원문 문서

- [ ] **Step 1: 이동 전 원문 수를 기록한다**

Run: `rg --files -g '*.md' -g '!README.md' -g '!Home.md' -g '!docs/**' | wc -l`

Expected: 53

- [ ] **Step 2: 주차 기준으로 원문을 이동한다**

Move 0701~0703 to Week 1; 0706~0710 to Week 2; 0713~0716 to Week 3; 0720~0724 to Week 4; 0727~0731 to Week 5; 0803~0807 to Week 6; 0810~0816 to Week 7; 0817~0823 to Week 8; 0824~0827 to Week 9; and 0831 to Week 10. Move `week1.md` through `week6.md` and `project.md` to `review/weekly/`, then remove `Home.md`.

- [ ] **Step 3: 이동 결과를 확인한다**

Run: `test ! -e Home.md && test -f review/weekly/project.md && find review/daily -type f -name '*.md' | wc -l`

Expected: exit 0 and 46

### Task 2: 문서형 README와 주차 인덱스 작성

**Files:**
- Create: `README.md`
- Create: `review/daily/week1/README.md` through `review/daily/week10/README.md`

**Interfaces:**
- Consumes: Task 1의 문서 경로
- Produces: 루트 및 주차별 탐색 진입점

- [ ] **Step 1: 링크 검증 명령을 먼저 실행한다**

Run: `test -f README.md`

Expected: FAIL because root README does not exist

- [ ] **Step 2: README와 10개 주차 인덱스를 작성한다**

README에 저장소 소개, Week 1~6 주차 회고 링크, `프로젝트 주차 회고 (Week 5–9)` 링크, Week 1~10 일일 회고 인덱스 링크를 넣는다. 각 주차 인덱스에는 해당 폴더의 날짜별 회고 링크를 오래된 날짜부터 넣고 루트 README로 돌아가는 링크를 넣는다.

- [ ] **Step 3: 파일 존재와 링크 대상을 검증한다**

Run: `ruby -e 'files=Dir["README.md", "review/**/*.md"]; links=files.flat_map { |f| File.read(f).scan(/\[[^\]]+\]\(([^)#]+)(?:#[^)]+)?\)/).flatten.map { |p| [f,p] } }; bad=links.reject { |f,p| File.exist?(File.expand_path(p, File.dirname(f))) }; abort("broken links: #{bad.inspect}") unless bad.empty?; puts "all links valid"'`

Expected: `all links valid`

### Task 3: 구조 완성 검증 및 커밋

**Files:**
- Modify: 이동된 Markdown 및 새 인덱스 문서

**Interfaces:**
- Consumes: Task 1~2의 최종 파일 구조
- Produces: 검증된 README 중심 문서 저장소

- [ ] **Step 1: 원문 수와 Git 상태를 검증한다**

Run: `test "$(find review -type f -name '*.md' ! -name README.md | wc -l | tr -d ' ')" = 53 && git diff --check && git status --short`

Expected: exit 0; 원문 53개, 공백 오류 없음

- [ ] **Step 2: 변경 사항을 커밋한다**

Run: `git add README.md review Home.md docs/superpowers && git commit -m "docs: organize reviews and add README"`

Expected: README와 `review/` 구조를 포함한 커밋 1개
