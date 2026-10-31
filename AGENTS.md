# AI 에이전트 작업 지침

이 저장소는 책 『The State of Vibe Coding』의 원고와 빌드 도구다. AI 에이전트는 작업 전에 이 파일과 요청받은 파일을 읽는다.

## 집필 기준

책 본문의 집필, 문체, 출처와 리뷰 기준은 [WRITING_STYLE.md](docs/WRITING_STYLE.md)를 따른다.

## 구조와 수정 범위

- `ko/`는 한국어판 Quarto book이며 기본 원문이다. `en/`은 영어판이며 대부분 번역 생성물이다.
- 집필 단위는 `ko/sections/NN-M-slug.qmd`의 꼭지와 `ko/glossary/slug.qmd`의 개념 사전 항목이다. 담당과 범위는 [TOPICS.md](TOPICS.md)를 따른다. 영어가 원문인 꼭지는 `en/`의 대응 파일을 쓴다.
- 본문은 섹션 파일에 쓴다. 챕터 파일은 리드 문단과 `{{< include ../sections/... >}}`로 구성된다.
- 포함되는 섹션과 개념 사전 파일에는 YAML frontmatter를 넣지 않는다. 원문 파일의 첫 줄은 `<!-- authoritative-lang: ko -->` 또는 해당 원문 언어를 표시하는 주석이다. 챕터 파일은 frontmatter를 사용한다.
- 섹션 제목은 `## 제목 {#sec-slug}` 형태다. 기존 앵커와 include 경로를 보존하고 Quarto 콜아웃의 `:::` 짝을 맞춘다.
- `MACHINE-TRANSLATED` 마커가 있는 파일은 직접 수정하지 않는다. 해당 꼭지의 원문을 수정하고 `tools/translate`로 번역을 갱신한다. 영어가 원문이면 한국어판이 번역 생성물이 될 수 있다.
- 원문 언어는 `authoritative-lang` 설정으로 확인한다. 언어 설정 변경은 저자 및 티칭 팀과 조율한다.
- 챕터를 추가하거나 삭제할 때는 `ko/_quarto.yml`과 `en/_quarto.yml`을 모두 갱신한다. 섹션 추가는 챕터의 include와 TOPICS.md도 갱신한다.
- 요청받은 담당 범위만 수정한다. 다른 저자의 원고나 책 전체를 일괄 수정하지 않는다. 다른 꼭지의 변경은 해당 저자와 조율하고 PR에서 검토한다.

## 명령과 확인

```bash
tools/build html ko
tools/build
tools/translate
tools/new-chapter 11-slug "제목"
```

원고 편집 후에는 최소한 `tools/build html ko`를 확인한다. 영어 원문을 편집했다면 `tools/build html en`도 확인한다. 전체 HTML과 PDF 검증에는 `tools/build`를 사용한다. 실행하지 못한 확인은 실행한 것처럼 보고하지 말고 이유를 기록한다.

커밋, 푸시, PR 생성과 외부 공유에 관한 사용자의 지시를 따른다.

## 저자와 조장의 역할

각 저자는 자기 꼭지의 주장, 근거, 코드와 AI 사용 결과를 확인한다. 조장은 장 전체 내용을 종합 관리하고 꼭지가 유기적으로 연결되도록 조율한다. 조별 담당과 조장 명단은 확인된 운영 명단을 따른다. 이름의 나열 순서로 조장을 추정하지 않는다.

조장이 장의 리드 문단과 꼭지 순서에 대한 수정안을 정리하면 티칭 팀이 챕터 파일에 반영할 내용을 검토한다. 저자의 주장과 해석이 바뀌는 변경은 해당 저자에게 확인받는다.

## 수업 맥락

서울대학교 데이터사이언스 특강 〈바이브 코딩〉의 공동 집필 프로젝트다. 집필 상태 콜아웃과 담당 표기는 수업 운영 장치이므로 임의로 지우지 않는다. 수업 정책은 [SYLLABUS.md](SYLLABUS.md), 기여 절차는 [CONTRIBUTING.md](CONTRIBUTING.md), 책 소개는 [README.md](README.md)를 참고한다.
