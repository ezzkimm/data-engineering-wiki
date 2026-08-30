# README Wiki Structure Design

## Goal

GitHub 저장소의 첫 화면을 `README.md`로 제공하고, 학습 기록을 역할별 폴더로 정리해 위키처럼 탐색할 수 있게 한다.

## Chosen Approach

깔끔한 문서형 첫 화면을 사용한다. README는 저장소 소개, 핵심 문서로 가는 바로가기, 주차별 회고, 월별 일일 회고, 프로젝트 회고만 표시한다. 회고 원문은 README에 중복하지 않는다.

## File Structure

```text
README.md
docs/
  retrospectives/
    daily/
      2026-07/
      2026-08/
    weekly/
      week1.md ... week6.md
  projects/
    ddareungi-retrospective.md
```

`Home.md`는 제거한다. 기존 루트의 일일 회고 문서는 해당 월 폴더로, 주차별 회고 문서는 `weekly`로, `project.md`는 `projects`로 이동한다.

## README Content

- 제목과 한 줄 소개
- `주차별 회고`, `프로젝트 회고` 바로가기
- Week 1부터 Week 6까지의 개별 링크
- 2026년 7월과 8월 일일 회고 인덱스 링크

월별 인덱스 문서는 해당 월의 모든 일일 회고를 날짜순으로 링크한다. 이 구조는 README를 짧게 유지하면서도 모든 기록을 두 번 이내의 클릭으로 찾게 한다.

## Link Rules

- 저장소에서는 GitHub 상대 링크 문법을 사용한다.
- README에서는 `docs/...`를 기준으로 링크한다.
- 월별 인덱스에서는 같은 폴더의 회고 파일로 링크한다.
- 각 회고 원문은 내용을 바꾸지 않는다.

## Validation

- 이동 전후 Markdown 원문 파일 수가 동일해야 한다.
- README 및 월별 인덱스의 링크 대상이 모두 존재해야 한다.
- `README.md`가 루트에 존재하고 `Home.md`는 없어야 한다.
