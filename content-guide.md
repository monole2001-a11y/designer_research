# Content Guide
## `index.html` / `study-abroad.html`

---

## 1. 문서 개요

| 항목 | 내용 |
|------|------|
| 파일명 | `index.html`, `study-abroad.html`, `product-designer-outlook-2026.html` |
| 목적 | 프로덕트 디자이너 시장 전망과 SVA/유학/NIW 의사결정을 탭형 웹페이지로 분리 제공 |
| 주요 독자 | 커리어 전환·취업 준비 중인 디자이너, 유학/NIW 검토자, 채용 담당자, 교육 기관 |
| 기준일 | 2026년 5월 25일 |
| 언어 | 한국어 (섹션 8–9 테이블 헤더·기업명 일부 영어) |
| 웹 페이지 구조 | `index.html` = 시장 전망, `study-abroad.html` = 유학/SVA/NIW |

---

## 2. 전체 섹션 구조

```
index.html — 프로덕트 디자이너 전망 탭
├── 섹션 1  — 핵심 시장 지표
├── 섹션 2  — 시장 현황 및 채용 트렌드
├── 섹션 3  — AI가 직업에 미치는 영향
├── 섹션 4  — 연봉 현황
├── 섹션 5  — 미국 주요 도시별 채용 현황
├── 섹션 6  — 주니어~미드레벨 역량 심층 분석
├── 섹션 7  — 직급별 취업 난이도 전망
├── 섹션 8  — 프로덕트 디자인 변화 흐름
├── 섹션 9  — 빅테크·테크 기업별 레이오프 현황
└── 섹션 10 — 종합 전략 제언

study-abroad.html — 유학/SVA/NIW 탭
├── 섹션 1 — 석사 지원자를 위한 학교 & 학과 가이드 (미국)
└── 섹션 2 — 개인 의사결정: 삼성 잔류 vs SVA 유학 vs NIW

product-designer-outlook-2026.html — 전체 통합 백업본
```

---

## 3. 섹션별 상세 가이드

### 섹션 1 — 핵심 시장 지표

**목적:** 독자가 보고서 전체를 읽기 전에 핵심 수치 6개를 한눈에 파악하게 함.

**현재 데이터:**

| 지표 | 값 | 출처 |
|------|----|------|
| 미국 활성 채용 공고 | 98,465건 | Zippia 2026 |
| 2030년까지 성장률 | +15% | Zippia 2026 |
| 수요 증가 응답 조직 | 82% | Figma Survey 2026 |
| 미국 평균 연봉 | $102K | Zippia / UX Design Institute |
| AI 역량 필수 요구율 | 73% | Figma Survey 2026 |
| 시니어 수요 비율 | 56% | Figma Survey 2026 |

**업데이트 주기:** 연 1회 (연초 또는 상반기 주요 리포트 발표 후)

**업데이트 방법:** 각 `stat-card`의 `.value` 텍스트와 `.desc` 설명 수정. 색상(`--card-color`)은 지표 성격에 따라 유지.

---

### 섹션 2 — 시장 현황 및 채용 트렌드

**목적:** 채용 시장의 정성적 트렌드를 4개 인사이트 카드로 요약.

**현재 카드:**

1. **2026년 새 레이오프 물결** — AI 투자 재원 조달 패턴, 채용 동결 확산
2. **시니어 인재에 집중된 수요** — 56% vs 25% 수치
3. **크로스펑셔널 협업 능력 부상** — NNg 2026 State of UX 핵심 역량으로 명시 (특정 % 수치 없음)
4. **하이브리드 근무 표준화** — 완전 원격 감소

**업데이트 시 주의:** 첫 번째 카드(레이오프)는 섹션 8의 실수치와 일관성을 유지해야 함. 두 곳을 동시에 수정할 것.

---

### 섹션 3 — AI가 프로덕트 디자이너 직업에 미치는 영향

**목적:** AI 도입의 양면성(대체 위험 vs. 가치 상승)을 데이터와 함께 제시.

**구성:**
- 좌측 바차트: AI 도입 후 디자이너 체감 변화 (Figma 서베이)
- 우측 바차트: AI 관련 채용 공고에서 가장 요구되는 역량 순위
- 위험/기회 비교 카드 (risk-grid)
- 핵심 메시지 박스

**핵심 메시지 (변경 불가 방침):** "AI는 디자이너를 대체하는 것이 아니라 '분류'하고 있다." — 이 프레이밍이 보고서 전체의 논조를 설정함.

**바차트 수치 업데이트:**
- `width:XX%`의 XX 값과 `.pct` 텍스트 값이 일치해야 함
- 100%가 아닌 순위 데이터(1위/2위...)는 상대 비율로 막대 길이 표현

---

### 섹션 4 — 연봉 현황

**목적:** 미국과 한국의 직급별 연봉 범위를 테이블로 비교.

**미국 데이터 출처:** UX Design Institute, Zippia, Glassdoor

**한국 데이터 출처:** levels.fyi (서울), 프라임 커리어, groupby.careers

**현재 데이터:**

| 지역 | 직급 | 연봉 범위 |
|------|------|-----------|
| 미국 | Junior | $65K–$85K |
| 미국 | Mid | $85K–$115K |
| 미국 | Senior | $115K–$150K |
| 미국 | Staff/Principal | $150K–$200K+ |
| 한국 | 신입 (0-2년) | 3,200–3,800만 원 |
| 한국 | 주니어 (2-4년) | 3,800–5,000만 원 |
| 한국 | 미드 (4-6년) | 5,000–7,000만 원 |
| 한국 | 시니어 (6년+) | 8,000만–1억 4천만 원 |

**참고 문구:** levels.fyi 기준 서울 프로덕트 디자이너 전체 중앙값은 ₩82,266,524 (~$59,600 USD). 구글코리아·삼성 등 대형 글로벌사 시니어는 $145K–$166K+ 사례 보고 있으나 표본 수 적음. 국내 IT 기업(카카오·네이버 등) 시니어 기준 ₩8,000만–₩1억 4,000만 (프라임 커리어 출처).

---

### 섹션 5 — 주니어~미드레벨 요구 역량 심층 분석

**목적:** 실제 채용 현장(LinkedIn JD, 커뮤니티 피드백)에서 요구하는 역량을 직급별로 구체화.

**데이터 출처:** LinkedIn 채용 공고 분석, CareerFoundry, UXfolio, Her UX Path, Smashing Magazine, UX Playbook (2026)

**구성:**

#### 주니어 역량 카드 (0–2년)

| 역량 | 태그 |
|------|------|
| Figma 완숙도 (Auto-layout, 컴포넌트, Variables) | MUST |
| AI 도구 워크플로우 통합 | 2026 NEW |
| HTML/CSS 기초 | 차별화 |
| 유저 리서치 기초 (인터뷰→사용성 테스트) | MUST |
| 페르소나 & 저니맵 | MUST |
| WCAG 2.2 접근성 | MUST |
| 도메인 집중 전략 | 강력 권장 |
| 피드백 수용 & 빠른 이터레이션 | MUST |

#### 미드레벨 역량 카드 (2–5년)

| 역량 | 태그 |
|------|------|
| 디자인 시스템 구축 & 운영 | MUST |
| AI 제품 경험 설계 (설명가능성, 신뢰 패턴) | 2026 NEW |
| 엔지니어 핸드오프 최적화 | MUST |
| 유저 리서치 주도 | MUST |
| 임팩트 지표 정의 & 측정 | MUST |
| A/B 테스트 설계 | 차별화 |
| 크로스펑셔널 협업 주도 | MUST |
| 도메인 심화 전문성 | 강력 권장 |

#### 포트폴리오 합격 기준 (5개 체크리스트 항목)

1. 3–5개 케이스 스터디만 (품질 > 수량)
2. 프로세스 + 시각 품질 모두 필요
3. 임팩트 지표 필수 제시
4. AI 활용 방식 명시 (78% 채용담당자 평가)
5. 3분 안에 포지셔닝이 읽혀야

#### 채용 담당자가 보는 것 (3개 recruiter-tip)

- 처음 5초
- 케이스 스터디 진입 후 30초
- 주니어 vs 미드레벨 구분 기준

#### 직급별 도구 우선순위

- 주니어 필수: Figma, Figma AI, Maze/Useberry, Miro/FigJam, Notion, Claude/ChatGPT
- 미드레벨 추가: Figma Variables/Dev Mode, v0/Figma Make, Amplitude/Mixpanel, Protopie, Framer, Lottie/Rive

---

### 섹션 6 — 직급별 취업 난이도 전망

**목적:** 4단계 직급의 취업 난이도·차별화 요소·전망을 한 테이블로 정리.

**현재 데이터:**

| 직급 | 난이도 | 핵심 차별화 | 전망 |
|------|--------|-------------|------|
| 신입/주니어 (0-2년) | 매우 치열 (red) | AI 도구 능숙도, 포트폴리오, 사이드 프로젝트 | 진입 장벽 높음, 공급 과잉 |
| 미드레벨 (2-5년) | 경쟁적 (yellow) | 임팩트 수치화, 디자인 시스템, 도메인 전문성 | 꾸준한 수요, 안정적 |
| 시니어 (5-8년) | 수요 우위 (green) | 전략적 사고, 조직 영향력, AI 제품 리드 | 채용 수요 지속 증가 |
| Staff/Principal (8년+) | 희소 고가치 (purple) | C-suite 커뮤니케이션, 사업 전략 연계 | 파격적 처우, 희소 |

---

### 섹션 7 — 프로덕트 디자인의 변화 흐름

**목적:** 2022년 레이오프 빙하기부터 2030년 성장 국면까지 시간순으로 맥락 제공.

**타임라인 항목 (4개):**

| 기간 | 닷 색상 | 핵심 내용 |
|------|---------|-----------|
| 2022–2023 | `#f76b6b` (빨강) | 대규모 레이오프, 채용 빙하기 |
| 2025 | `#f7a24b` (주황) | 시장 안정화, 주니어 회복 지연 |
| 2026년 1–5월 | `#f76b6b` (빨강) | 2차 레이오프 물결, AI 투자 재원 조달 |
| 2026 하반기–2030 | `#56cfb2` (초록) / `#7c6ef7` (보라) | AI 네이티브 역할 분화, 성장 국면 |

**섹션 8과의 연계:** 2026년 1–5월 항목의 수치(143,000명, Q1 81,700명 등)는 섹션 8 데이터와 일치해야 함.

---

### 섹션 8 — 빅테크 기업별 2026 레이오프 현황

**목적:** 기업별 실수치·시기·영향 팀·지역을 하나의 테이블로 정리. 가장 자주 업데이트가 필요한 섹션.

**기준일:** 2026년 5월 25일

**현재 기업 목록 (12개):**

| 회사 | 감원 규모 | 시기 | 주요 거점 |
|------|-----------|------|-----------|
| Oracle | 20,000–30,000 (18%) | Mar–Apr 2026 | Austin TX / Santa Clara CA |
| Amazon | ~16,000 | Jan–May 2026 | Seattle WA / New York NY |
| Meta | 8,000 직접 + 6,000 공석 미충원 | May 20, 2026 | Menlo Park CA / Seattle WA |
| Microsoft | ~9,000 (<4% 글로벌) | Apr 23, 2026 | Redmond WA / New York NY |
| Block | ~4,000 (~40%) | Mar 2026 | San Francisco CA |
| Cisco | ~4,000 (5%) | Q1 2026 | San Jose CA / Milpitas CA |
| Intuit | ~3,000 (17%) | May 20–22, 2026 | Mountain View CA |
| LinkedIn | ~875 (5%) | May 22, 2026 | Mountain View CA |
| Salesforce | ~1,000 | May 2026 | San Francisco CA |
| Snap | ~1,000 | H1 2026 | Santa Monica CA |
| Alphabet (Google) | ~1,500 | Jan–May 2026 | Mountain View CA / New York NY |
| Adobe | ~100 | H1 2026 | San Jose CA |

**데이터 업데이트 출처 (우선순위 순):**
1. [Layoffs.fyi](https://layoffs.fyi/) — 실시간 트래커
2. [TrueUp](https://www.trueup.io/layoffs) — 집계 통계
3. [TechCrunch](https://techcrunch.com) — 공식 발표 확인
4. [Crunchbase](https://news.crunchbase.com/startups/tech-layoffs/) — 연간 추적
5. [Computerworld](https://www.computerworld.com/article/3816579/tech-layoffs-this-year-a-timeline.html) — 타임라인

**지역별 데이터 (US, 5/25 기준):**

| 지역 | 수치 | 근거 |
|------|------|------|
| Seattle, WA | 16,590명 (미국 1위) | Amazon + Microsoft 거점 |
| San Francisco | 9,395명 | SF 오피스 공실률 36.7% (Q1 2026) |
| Menlo Park | 1,500명 | Meta 본사 직접 감원 |
| Mountain View | 800+ | LinkedIn + Intuit 동주간 동시 발표 |
| Austin TX | 20K–30K | Oracle 단일 이벤트 (단일 도시 최대) |

**AI 연계 통계:**
- 2026 YTD: 142,985명 / 339개사 / 하루 평균 993명
- Q1 2026: 81,700명 (2023년 초 이후 최고 분기치)
- AI 명시 감원 비율: 20.4% (2025년 8% 미만 → 2.5배)
- Big 4 AI capex: $725B (전년比 +75%)

---

### 섹션 9 — 석사 지원자를 위한 학교 & 학과 가이드 (미국)

**목적:** 미국 HCI/프로덕트 디자인 석사 프로그램 7개의 학비·취업 성과·특징 비교.

**현재 학교 목록:**

| 학교 | 프로그램 | 총 학비 | 첫 연봉 중앙값 | 비고 |
|------|----------|---------|----------------|------|
| Carnegie Mellon (CMU) | MHCI / MDes | ~$86,250 | $110K–$135K | 세계 최초 HCI 석사, 합격률 ~10–15% |
| Stanford | MS HCI / d.school MDes | ~$65K–$80K/년 | $150K+ | 97% 6개월 내 취업, SV 네트워크 최강 |
| Georgia Tech | MS-HCI | ~$14K–$30K (총액) | $95K–$115K | Best ROI, 공립대 |
| U Michigan | MSI – UX R&D | ~$30K–$52K (총액) | ~$92K | 95% 취업만족도, 리서치 특화 |
| Parsons | MFA Design & Tech / MPS | ~$55K–$70K/년 | — | NYC 네트워크, 1년 MPS 옵션 |
| RISD | MFA Industrial / Digital+Media | ~$60K–$66K/년 | — | Apple 하드웨어팀 선호 학교 |
| SCAD | MFA UX / Service Design | ~$36K–$42K/년 | $75K–$90K | 온라인 옵션, Google·IBM 직접 리크루팅 |
| SVA | MFA Interaction Design (IxD) | ~$123,380 총액 ($61,690/년 × 2) | ~$90K–$110K (추정) | NYC IxD 전문, Inclusive Design 강점, 공식 취업 데이터 미발행 |

**연봉 바차트 순서:** Stanford > CMU > Georgia Tech > Michigan > SCAD

**데이터 출처:**
- 학비: 각 학교 공식 홈페이지 (CMU: `hcii.cmu.edu/academics/mhci/tuition`)
- 연봉: PayScale 2026, Glassdoor 집계
- 취업률: Stanford (공식 97%), U Michigan UMSI (공식 95%)
- 합격률: CMU ~10–15% (anthonyteo.com blog 분석), Stanford ~<10% (추정)

**전략 팁 4개:**
1. Best ROI → Georgia Tech
2. Bay Area & Big Tech → CMU 또는 Stanford
3. Research Path → U Michigan MSI
4. 포트폴리오 > 학교 이름

---

### 섹션 10 — 종합 전략 제언

**목적:** 보고서의 핵심 인사이트를 6개의 실행 가능한 액션으로 압축.

**현재 6개 항목 요약:**
1. AI 도구 매일 통합 + 포트폴리오에 명시 (73% 필수)
2. 비즈니스 임팩트 지표 중심 케이스 스터디
3. 주니어: 특정 버티컬 도메인 전문성
4. 시니어: AI 워크플로우 도입 주도 포지셔닝
5. 디자인 시스템 경험 (소규모 고효율 팀 트렌드)
6. AI가 대체 어려운 인간적 역량 개발

**이 섹션은 논조(Tone)의 마무리이므로 사실 데이터 업데이트보다는 시장 트렌드 논조 변화 시에만 수정한다.**

---

### 섹션 11 — 개인 의사결정 / SVA 재무 시뮬레이션

**목적:** 삼성전자 잔류, SVA 진학, NIW 준비의 선택지를 재무·비자·커리어 관점에서 비교한다.

**현재 핵심 가정:**

| 항목 | 값 | 비고 |
|------|----|------|
| SVA IxD 2년 학비 | 약 $123,380 | 2026–27 tuition 기준, fees/living cost 제외 |
| 국비유학생 장학금 | $100,000 | 학비 대부분 상쇄 |
| 학비 순부담 | 약 $23,380 | 학비 기준 |
| NYC 2년 생활비 | $70,000–$90,000 | 렌트에 따라 크게 변동 |
| 저비용 쉐어하우스 생활비 2년 | $48,000–$62,000 | Queens, Brooklyn 외곽, New Jersey 일부 지역 룸 쉐어 가정 |
| 보험·재료·정착비 | $8,000–$12,000 | 버퍼성 비용 |
| 장학금 반영 후 순현금 필요액 | $101,000–$125,000 | 학비 잔액 + 생활비 + 기타 비용 |
| 저비용 거주 시나리오 순현금 필요액 | $79,000–$97,000 | 기본 시나리오 대비 약 $22K–$28K 절감 |
| 추가 대출 | 5천만 원 (~$36,200) | 환율 1,380원/$ 가정 |

**상환 시뮬레이션:** 이자 제외, NYC 세후 월 실수령 추정 기준. $90K/$110K/$130K starting salary에서 월 실수령 10% 또는 15% 상환 시 기간을 비교한다.

**거주비 절감 시나리오:** 외곽/쉐어하우스 옵션은 재무 방어력을 높이지만, 통학 시간·안전성·룸메이트 리스크·네트워킹 시간 감소를 함께 고려해야 한다.

**업데이트 시 주의:**
- 환율, SVA tuition, NYC living cost가 바뀌면 전체 비용 테이블과 상환 바차트를 함께 수정.
- 국비유학생 지원금이 생활비까지 별도 포함되는 경우 순현금 필요액을 낮춰야 함.
- 이 섹션은 법률·투자 조언이 아니라 개인 의사결정 프레임으로 유지.

---

## 4. Sources 섹션

보고서에 사용된 모든 출처의 목록. 새 데이터를 추가하면 반드시 이 섹션도 업데이트.

**현재 출처 목록 (총 21개):**

```
Figma Blog — Why Demand for Designers Is on the Rise
Nielsen Norman Group — State of UX 2026
UX Design Institute — The UX Job Market in 2026
Zippia — Product Designer Job Outlook And Growth In The US [2026]
Medium/Bootcamp — Will the 2026 Product Design Job Market Be Bullish?
Designlab — The State of AI in UX & Product Design: 2026
Gozade — Is AI Replacing Product Designers?
U.S. Bureau of Labor Statistics — Web Developers and Digital Designers Outlook
UX Design Institute — UX Designer Salaries in the US: Updated for 2026
levels.fyi — 서울 프로덕트 디자이너 연봉
프라임 커리어 — 프로덕트 디자이너 연봉 2025 현실 수치
LogRocket — Figma AI in 2026
Lenny's Newsletter — State of the product job market in early 2026
Layoffs.fyi — Tech Layoff Tracker
TrueUp — Layoffs Tracker
TechSpot — Tech layoffs pass 100,000 in 2026
CNBC — 20,000 job cuts at Meta, Microsoft
Crunchbase — Tech Layoffs 2024, 2025 and 2026
Computerworld — Tech layoffs 2026: A timeline
Invezz — Big Tech layoffs 2026: Amazon, Meta, Microsoft and the AI trade-off
Kore1 — Oracle Layoffs 2026
Animation Career Review — Top 25 Graduate UX/UI/HCI Schools
Uxcel — 9 Best UX Design Schools in 2026
DesignWhine — UX Design Education in South Korea
EduRank — Best UX/UI Design Schools in South Korea 2026
The GradCafe — Top 10 Best UX Design Graduate Programs in 2026
Smashing Magazine — UX And Product Designer's Career Paths In 2026
Her UX Path — How to Land a Junior UX Designer Job in 2026
UXfolio — UX Portfolio Playbook: What Recruiters Actually Look For
UX Playbook — 6 UX Portfolio Rules That Actually Get You Hired in 2026
Muzli — How to Build a UX Portfolio That Actually Gets You Hired
CareerFoundry — The Ultimate Junior Product Designer Career Guide
CourseCareers — Core Skills Every Junior UI/UX Designer Needs
```

---

## 5. 업데이트 주기 가이드

| 섹션 | 업데이트 빈도 | 트리거 |
|------|-------------|--------|
| 섹션 1 — 핵심 지표 | 연 1회 | Figma Annual Survey, BLS 연간 발표 |
| 섹션 2 — 시장 현황 | 반기 1회 | 주요 트렌드 리포트 발표 |
| 섹션 3 — AI 영향 | 분기 1회 | AI 도구 대형 업데이트, 새 서베이 |
| 섹션 4 — 연봉 | 연 1회 | Glassdoor, levels.fyi 연간 보고서 |
| 섹션 5 — 역량 | 반기 1회 | LinkedIn JD 트렌드 변화 |
| 섹션 6 — 난이도 | 연 1회 | |
| 섹션 7 — 타임라인 | 주요 이벤트 발생 시 | 대형 레이오프, AI 도구 출시 |
| 섹션 8 — 레이오프 | 즉시 (사건 발생 시) | Layoffs.fyi 신규 항목, 공식 발표 |
| 섹션 9 — 학교 | 연 1회 (가을) | 입학처 공식 학비 업데이트 |
| 섹션 10 — 학교/학비 | 연 1회 (가을) | 입학처 공식 학비 업데이트 |
| 섹션 11 — 개인 의사결정/재무 | 분기 1회 또는 조건 변경 시 | 환율, 장학금, 대출, 생활비, 진학 여부 변경 |
| 섹션 12 — 전략 | 시장 논조 변화 시 | |

---

## 6. 새 섹션 추가 방법

1. 기존 섹션 뒤, `<!-- Divider -->` 앞에 삽입
2. 섹션 번호(`.num`) 이후 섹션 모두 +1 수정
3. 해당 섹션의 데이터 출처를 `Sources` 섹션에 추가
4. `content-guide.md`의 섹션별 상세 가이드에 항목 추가

---

## 7. 데이터 정확성 원칙

- **1차 출처 우선:** 기업 공식 발표문, BLS 정부 데이터, 대학 공식 사이트
- **2차 출처:** Layoffs.fyi, TrueUp, Glassdoor, PayScale (집계 서비스)
- **3차 출처:** TechCrunch, CNBC, Computerworld (보도 기사)
- 수치에 확실하지 않은 경우 `~` 또는 범위(`20,000–30,000`)로 표기
- 기준일은 항상 본문 상단과 Hero 메타 영역에 명시
- 한국 데이터 수치는 가능하면 원화(만원) 단위로 표기하고 USD 환산은 주석으로 처리
