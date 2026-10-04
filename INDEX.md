# 공통 규칙 색인

이 INDEX.md가 있는 폴더가 공통 루트다. 루트 문서는 진입점, `agent-rules/`는 프로젝트 공통 규칙, 각 프로젝트 안의 MD는 그 프로젝트의 상세 규칙이다. 경로는 이 파일의 위치 기준이며 드라이브·루트 폴더명·현재 작업 디렉토리에 의존하지 않는다. Markdown 링크는 링크가 있는 문서의 위치 기준으로 해석한다.

## 필수 읽기

매 작업 `agent-rules/core.md`를 읽고, 아래에서 해당하는 문서를 추가로 읽는다. 이미 읽은 내용은 변경되지 않았다면 다시 읽지 않는다.

| 작업 | 필수 문서 |
|---|---|
| 구현·수정·디버깅·검증·리뷰 | [workflow.md](agent-rules/workflow.md) |
| 소스·API·공용 로직 수정 | [coding.md](agent-rules/coding.md) |
| 화면·CSS·JS·화면 데이터·인증 흐름 수정 | [ui.md](agent-rules/ui.md) + coding.md + workflow.md |
| 인증·권한·개인정보·로그·시크릿 | [security.md](agent-rules/security.md) |
| DB·DDL·이관·배치·분산 상태·외부 API | [data-integration.md](agent-rules/data-integration.md) + security.md |
| 빌드·배포·기동·장애·성능·인프라 | [operations.md](agent-rules/operations.md) + security.md |
| 문서·PPT·엑셀 등 산출물 | [artifacts.md](agent-rules/artifacts.md) |
| 규칙 자체의 추가·수정 | [maintenance.md](agent-rules/maintenance.md) |

## 프로젝트 지침 탐색

1. 하위 프로젝트에서 시작했다면 상위 폴더를 따라 `INDEX.md`와 `agent-rules/core.md`가 함께 있는 공통 루트를 찾는다. 고정 절대경로나 `agent`라는 폴더명을 가정하지 않는다. 실제 대상 프로젝트 루트도 확인하고 다른 프로젝트의 기술·경로·정책을 가져오지 않는다.
2. 프로젝트 루트부터 수정 파일의 부모까지 해당 경로의 `AGENTS.md`·`CLAUDE.md`를 확인한다. 같은 내용은 중복 로딩하지 않는다.
3. 프로젝트 색인과 지침에서 연결한 상세 MD를 작업 주제에 맞춰 읽는다. 모든 프로젝트의 모든 MD를 읽지 않는다.
4. 필수 참조가 없으면 누락을 밝힌다. 파일명·경로를 추정해서 대신 읽거나 내용을 꾸미지 않는다.

상위 시스템·도구 제약을 준수한다. 현재 사용자의 명시적 지시가 과거 선호보다 우선한다. 프로젝트 상세 지침은 공통 원칙을 구체화하며, 명시된 프로젝트 예외만 해당 범위에 적용한다. 같은 범위의 충돌은 최신 명시적 정정을 확인한다. 근거로 해소되지 않고 작업 결과에 영향을 주면 해당 판단만 확인하고 독립 작업은 계속한다.

정리 근거와 제외 항목은 `agent-rules/maintenance/analysis.md`에 있다. 일반 작업에서는 읽지 않는다.

## Git 포함 범위

루트 [.gitignore](.gitignore)는 기본적으로 전부 제외하고 `.gitignore`, `AGENTS.md`, `CLAUDE.md`, `INDEX.md`, `agent-rules/`와 그 내부 파일만 허용한다. 하위 프로젝트는 각자 별도 저장소로 관리하며 공통 규칙 저장소에 포함하지 않는다. 새 공통 지침은 `agent-rules/`에 둔다. 프로젝트를 포함시키려고 제외 규칙을 풀거나 `git add -f`로 우회하지 않는다.

이미 추적 중인 파일에는 ignore가 소급 적용되지 않는다. 그런 파일이 있으면 확인 결과와 추적 해제 명령만 제공하고 Git 상태 변경은 직접 실행하지 않는다.
