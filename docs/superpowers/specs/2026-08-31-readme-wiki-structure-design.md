# README Wiki Structure Design

## Goal

GitHub 저장소의 첫 화면을 `README.md`로 제공하고, 학습 기록을 역할별 폴더로 정리해 위키처럼 탐색할 수 있게 한다.

## Chosen Approach

깔끔한 문서형 첫 화면을 사용한다. README는 저장소 소개, 핵심 문서로 가는 바로가기, 주차별 회고, 주차별 일일 회고만 표시한다. 회고 원문은 README에 중복하지 않는다.

## File Structure

```text
README.md
review/
  daily/
    week1/ ... week10/
  weekly/
    week1.md ... week6.md
    project.md
```

`Home.md`는 제거한다. 기존 루트의 일일 회고 문서는 해당 주차 폴더로, 주차별 회고 문서와 `project.md`는 모두 `weekly`로 이동한다. 프로젝트 회고는 별도 폴더를 만들지 않는다.

일일 회고의 주차는 월요일~일요일 기준으로 나눈다. 7월 1~3일은 Week 1, 7월 6일부터는 매주 월요일에 다음 주차가 시작한다. 8월 31일 기록은 Week 10에 둔다.

`project.md`는 프로젝트 기간의 Week 5~9 기록과 최종 회고를 포함한 하나의 프로젝트 주차 회고 문서로 유지한다. README에서는 일반 Week 1~6 회고와 구분해 `프로젝트 주차 회고 (Week 5–9)`로 안내한다.

## README Content

- 제목과 한 줄 소개
- `주차별 회고`, `프로젝트 주차 회고` 바로가기
- Week 1부터 Week 6까지의 개별 링크
- Week 1부터 Week 10까지의 일일 회고 인덱스 링크

주차별 일일 회고 인덱스 문서는 해당 주의 모든 일일 회고를 날짜순으로 링크한다. 이 구조는 README를 짧게 유지하면서도 모든 기록을 두 번 이내의 클릭으로 찾게 한다.

## Link Rules

- 저장소에서는 GitHub 상대 링크 문법을 사용한다.
- README에서는 `review/...`를 기준으로 링크한다.
- 주차별 인덱스에서는 같은 폴더의 회고 파일로 링크한다.
- 각 회고 원문은 내용을 바꾸지 않는다.

## Validation

- 이동 전후 Markdown 원문 파일 수가 동일해야 한다.
- README 및 주차별 인덱스의 링크 대상이 모두 존재해야 한다.
- `README.md`가 루트에 존재하고 `Home.md`는 없어야 한다.
