# Claude Code Setup — 안전 요약

확인: 2026-06-13 19:36 KST  
범위: `CLAUDE.md`, `.claude/settings.json`, `.claude/settings.local.json`, `.claude/commands/*.md`

이 페이지는 Claude Code 설정을 웹에서 볼 수 있게 요약한 것이다. `settings.local.json`에는 로컬 파일 경로/개별 허용 명령이 포함될 수 있어 원문 전체를 싣지 않고 안전 요약만 둔다.

## 1. CLAUDE.md의 역할

`CLAUDE.md`는 Claude Code가 이 워크스페이스에서 Hermes처럼 동작하도록 하는 자동 로드 운영 지침이다.

핵심 내용:

- 기본 언어: 한국어.
- 날짜 기록: 항상 절대 날짜 `YYYY-MM-DD` 사용.
- 우선 도메인: 유학, 커리어, 업무 리서치, 투자.
- 세션 시작 루틴: `STATUS.md` 확인, `00_Inbox/` 새 항목 확인, 마감 임박 항목 우선 알림.
- 멀티 에이전트 동기화: Claude Code는 `CLAUDE.md`, Hermes Agent는 `HERMES.md`, AGENTS 표준 에이전트는 `AGENTS.md`를 읽으며, 운영 규칙 변경 시 `CLAUDE.md`와 `HERMES.md`를 함께 갱신.
- 파일 라우팅: Inbox, Profile, Projects, Research, Reports, Prompts, Archive로 역할 분리.
- `ref/` 취급: private local source material로 보고, 원문·요약·경로 목록을 승인 없이 외부 서비스에 넣지 않음.
- 투자 원칙: 매수/매도 지시 금지, 반대 근거와 무효화 조건 포함, 계좌/보유 수량/매입가 요구 금지.

## 2. `.claude/settings.json` 요약

전역에 가까운 Claude Code 권한 설정이다.

허용된 명령 범주:

- 파일/검색 확인: `ls`, `grep`, `rg`, `wc`
- git 읽기 작업: `git status`, `git log`, `git diff`, `git branch`

차단된 명령/파일 범주:

- 위험 명령: `sudo`, `rm -rf`, `rm -fr`, `git reset --hard`, `git clean`, `git push --force`, `git push -f`
- 민감 파일 읽기: `.env`, `.env.*`, `*.pem`, `*.key`, `*.p12`

의사결정 의미:

- Claude Code가 일반 탐색과 git 상태 확인은 할 수 있게 하되, 파괴적 명령과 인증/비밀키 파일 접근은 막는 구조다.

## 3. `.claude/settings.local.json` 안전 요약

로컬 예외 허용 설정이다. 원문에는 특정 웹 도메인과 로컬 `ref/` 파일 변환 명령이 들어 있어, 웹 공개 페이지에는 전체 원문을 싣지 않는다.

안전 요약:

- Hermes Agent 공식 문서 도메인에 대한 WebFetch 허용이 있다.
- 특정 로컬 참고 HTML을 텍스트로 변환하는 명령 허용이 있다.
- 이 설정은 워크스페이스 로컬 운용 편의를 위한 것이며, 공개 사이트에는 로컬 경로/명령 원문을 확장해 싣지 않는다.

## 4. Slash commands (`.claude/commands/*.md`)

현재 확인된 명령 7개:

| Command | 역할 |
| --- | --- |
| `/daily` | 오늘의 일간 리포트 생성 (04_Reports/YYYY-MM-DD_daily.md) |
| `/decision` | 의사결정 보조 후 결정 노트 저장 (03_Research/YYYY-MM-DD_decision-주제.md) |
| `/inbox` | 00_Inbox 항목을 분류·처리하고 프로젝트/리서치/리포트에 반영 |
| `/invest` | 투자 thesis 노트 생성·갱신 (리서치/기록 전용, 매수/매도 지시 금지) |
| `/research` | 리서치 수행 후 출처 포함 노트 저장 (03_Research/YYYY-MM-DD_topic.md) |
| `/start` | Hermes 세션 동기화 브리핑 — 상태, 인박스, 마감, 오늘의 추천 행동 |
| `/weekly` | 주간 리포트 생성 (04_Reports/YYYY-MM-DD_weekly.md) |

추가 확인: 슬래시 커맨드 원문에는 `/research`의 “공개/공식 출처 우선, 민감정보 검색 쿼리 금지” 원칙과 `/decision`의 “사실·가정·추정·추천 분리” 원칙이 명시되어 있다.

## 5. 이번 유학 결정 사이트에 주는 의미

- Claude Code 설정은 유학 결정 자체의 사실 근거가 아니라, **반복 가능한 운영 체계**다.
- `/research` 명령은 공개/공식 출처 우선, 민감정보를 쿼리에 넣지 않는 원칙을 명시한다. 이번 Pages 업데이트의 검색 원칙과 일치한다.
- `/decision` 명령은 사실·가정·추정·추천을 분리하고, 최종 결정은 사용자 몫으로 둔다. 이는 B(지금·국비·SVA) vs C(2년 후·자비·탑급 HCI)를 Hermes가 대신 결정하지 않고 게이트 증거로 보조한다는 원칙과 맞는다.
- `settings.json`의 위험 명령 차단은 이 예약 작업의 금지사항(삭제, force push, reset 등 금지)과 방향이 같다.

## 6. 공개 제외 원칙

이 사이트에는 다음을 싣지 않는다.

- 원본 `ref/` 파일 전문.
- 인증/config/session/runtime 파일.
- `.env*`, 토큰, API 키, 비밀번호, 개인 식별 가능한 보안 정보.
- 로컬 세션/로그/데이터베이스/gateway state.
- `settings.local.json`의 로컬 경로·명령 원문 전체.
