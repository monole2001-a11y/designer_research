# Design Guide
## `product-designer-outlook-2026.html`

---

## 1. Design Philosophy

단일 HTML 파일로 자체 완결되는 다크 테마 리서치 리포트. 외부 CSS 라이브러리·폰트 CDN 없이 인라인 `<style>` 블록만으로 구성된다. 모든 색상·여백·컴포넌트는 CSS Custom Properties로 관리하며, 값을 바꿀 때는 `:root` 블록만 수정한다.

---

## 2. Color System

모든 색상은 `:root`에 선언된 CSS 변수를 통해 사용한다. 직접 hex 값을 인라인으로 쓰지 않는다.

```css
:root {
  /* Backgrounds */
  --bg:       #0f0f13   /* 최하단 페이지 배경 */
  --surface:  #16161d   /* 카드, 패널의 기본 배경 */
  --surface2: #1e1e28   /* 테이블 헤더, hover 상태, 중첩 배경 */
  --border:   #2a2a38   /* 모든 구분선과 테두리 */

  /* Accent Colors */
  --accent:   #7c6ef7   /* Primary — 섹션 번호, 링크, 강조 */
  --accent2:  #56cfb2   /* Success/Positive — 긍정 지표, 상승 트렌드 */
  --accent3:  #f7a24b   /* Warning/Moderate — 중간 수준, 주의 필요 */
  --warn:     #f76b6b   /* Danger/Negative — 감원, 위험 지표 */

  /* Typography */
  --text:       #e8e8f0   /* 본문 주요 텍스트 */
  --text-muted: #888899   /* 설명, 부제목, 보조 정보 */
  --text-dim:   #555568   /* 매우 약한 텍스트 (출처, 라벨) */
}
```

### 색상 사용 원칙

| 상황 | 사용 변수 |
|------|-----------|
| 숫자가 긍정적 맥락 (성장률, 수요 증가) | `--accent2` |
| 숫자가 부정적 맥락 (감원, 위험) | `--warn` |
| 숫자가 중립·주의 맥락 (경쟁적, 보통) | `--accent3` |
| UI 강조, 섹션 번호, 버튼류 | `--accent` |
| 배지 배경 — 항상 해당 색상에 `rgba` + 투명도 15% 적용 | 예: `rgba(124,110,247,0.15)` |

---

## 3. Typography

```css
font-family: 'Pretendard', 'Apple SD Gothic Neo', -apple-system,
             BlinkMacSystemFont, 'Segoe UI', sans-serif;
```

Pretendard가 없는 환경에서는 시스템 기본 산세리프로 자연스럽게 폴백된다.

### 타입 스케일

| 용도 | 크기 | 굵기 | 비고 |
|------|------|------|------|
| Hero H1 | `clamp(28px, 4vw, 48px)` | 800 | 반응형 |
| 섹션 제목 H2 | `22px` | 700 | letter-spacing: -0.02em |
| 인사이트 카드 H3 | `16px` | 700 | |
| 스킬 이름 `.sname` | `13px` | 600 | |
| 본문 일반 | `14px` | 400 | line-height: 1.65 |
| 보조 설명 | `13px` | 400 | color: --text-muted |
| 라벨·태그 | `12px` | 600–700 | uppercase, letter-spacing: 0.06–0.12em |
| 마이크로 텍스트 | `10–11px` | 700 | 태그, 소섹션 레이블 |
| 통계 수치 `.value` | `32px` | 800 | letter-spacing: -0.03em |

---

## 4. Layout System

### 전체 레이아웃

```
.hero          — 전체 너비, 중앙 정렬 텍스트
.container     — max-width: 1100px, padding: 0 32px, 좌우 자동 마진
.section       — margin-top: 60px (섹션 간격)
```

### 그리드 클래스

```css
.stat-grid      /* repeat(auto-fit, minmax(200px, 1fr)) — 통계 카드 */
.insight-grid   /* repeat(auto-fit, minmax(300px, 1fr)) — 인사이트 카드 */
.two-col        /* 1fr 1fr — 2단 비교 레이아웃, 700px 이하에서 1단 */
.risk-grid      /* 1fr 1fr — 위험/기회 비교, 700px 이하에서 1단 */
```

### 반응형 브레이크포인트

| 브레이크포인트 | 변화 내용 |
|---------------|-----------|
| `≤ 700px` | `.two-col`, `.risk-grid` → 1단 |
| `≤ 600px` | `.hero` padding 축소 (48px 20px 40px), `.container` padding 축소 (0 16px), `.stat-grid` → 2단 고정 |

---

## 5. Component Library

### 5-1. Stat Card

주요 지표 숫자를 표시하는 카드. `--card-color` CSS 변수로 상단 accent 바 색상을 개별 지정한다.

```html
<div class="stat-card" style="--card-color: #7c6ef7;">
  <div class="label">레이블 텍스트</div>
  <div class="value">98,465</div>
  <div class="desc">부연 설명 텍스트</div>
</div>
```

- `.stat-grid` 안에 배치
- `--card-color`가 없으면 `--accent`로 폴백
- 카드 상단에 3px 컬러 바가 `::after`로 자동 생성됨

---

### 5-2. Insight Card

아이콘 + 제목 + 설명 형식의 정보 카드.

```html
<div class="insight-card">
  <span class="icon">📈</span>
  <h3>제목</h3>
  <p>설명 텍스트</p>
</div>
```

- `.insight-grid` 안에 배치
- 아이콘은 이모지 사용 (28px)

---

### 5-3. Salary Table (범용 데이터 테이블)

파일 내에서 가장 많이 쓰이는 테이블 래퍼. 이름은 `salary-table`이지만 어떤 표형 데이터에도 사용한다.

```html
<div class="salary-table">
  <table>
    <thead>
      <tr><th>컬럼1</th><th>컬럼2</th></tr>
    </thead>
    <tbody>
      <tr><td>값1</td><td>값2</td></tr>
    </tbody>
  </table>
</div>
```

- `border-radius: 14px`의 컨테이너가 테이블을 감싸는 구조
- hover 시 행 배경이 `--surface2`로 변경됨
- 마지막 행의 하단 보더는 자동 제거

---

### 5-4. Badge

인라인 상태 표시 태그. 4가지 시멘틱 색상.

```html
<span class="badge badge-green">수요 높음</span>
<span class="badge badge-yellow">경쟁적</span>
<span class="badge badge-red">매우 치열</span>
<span class="badge badge-purple">희소 고가치</span>
```

| 클래스 | 색상 | 의미 |
|--------|------|------|
| `badge-green` | `--accent2` (teal) | 긍정, 높은 수요 |
| `badge-yellow` | `--accent3` (amber) | 보통, 주의 |
| `badge-red` | `--warn` (red) | 부정, 위험, 치열 |
| `badge-purple` | `--accent` (purple) | 특별, 프리미엄, 희소 |

---

### 5-5. Horizontal Bar Chart

퍼센트·순위 데이터를 수평 막대로 시각화. `.bar-section` 컨테이너 안에 여러 `.bar-item` 배치.

```html
<div class="bar-section">
  <h3>차트 제목</h3>
  <div class="bar-item">
    <div class="bar-label">
      <span class="name">항목명</span>
      <span class="pct">73%</span>
    </div>
    <div class="bar-track">
      <div class="bar-fill" style="width:73%; --bar-color:#7c6ef7;"></div>
    </div>
  </div>
</div>
```

- `width` 값이 막대 길이를 결정 (퍼센트 값과 일치시킴)
- `--bar-color`로 막대 색상 개별 지정, 없으면 `--accent`
- `transition: width 0.6s ease` 애니메이션 내장

---

### 5-6. Skill Level Card

주니어/미드레벨 역량 비교에 사용하는 상세 스킬 카드.

```html
<div class="skill-level-card">
  <div class="slc-header">
    <div class="slc-title">직급 이름 <span class="badge badge-red">난이도</span></div>
    <div class="slc-sub">경력 범위 · 연봉 범위</div>
  </div>
  <div class="slc-section-label">카테고리 레이블</div>
  <div class="skill-item">
    <div class="sname">스킬명</div>
    <div class="sdesc">설명 텍스트</div>
    <span class="stag stag-must">MUST</span>
  </div>
</div>
```

**Skill Tag (`.stag`) 종류:**

| 클래스 | 색상 | 의미 |
|--------|------|------|
| `stag-must` | red/pink | 필수 요건 |
| `stag-plus` | teal | 차별화 요소 |
| `stag-new` | purple | 2026년 신규 요구사항 |

---

### 5-7. Portfolio Checklist

체크리스트 형식의 조건 목록.

```html
<ul class="port-checklist">
  <li>
    <span class="pc-icon">📁</span>
    <span><strong>굵은 핵심</strong> — 일반 설명 텍스트</span>
  </li>
</ul>
```

- 각 항목 사이 하단 보더 자동 생성 (마지막 항목 제외)
- 아이콘은 이모지

---

### 5-8. Recruiter Tip Box

왼쪽 accent 바가 있는 인용/팁 박스.

```html
<div class="recruiter-tip">
  <div class="rt-label">레이블</div>
  <p>본문 내용</p>
</div>
```

- `border-left: 3px solid var(--accent)` 로 시각적 강조
- 여러 개를 연속 배치 시 `margin-bottom: 10px` 자동 적용

---

### 5-9. Timeline

시간순 이벤트 나열.

```html
<div class="timeline">
  <div class="tl-item">
    <div class="tl-dot" style="background: #색상코드;"></div>
    <h4>기간 — 제목</h4>
    <p>설명</p>
  </div>
</div>
```

- `.tl-dot` 색상으로 심각도/단계 구분 (빨강→주황→보라→초록 순)
- 세로 연결선은 `.timeline::before`로 자동 렌더링

---

### 5-10. Pill List

태그 클라우드 형식의 스킬/도구 목록.

```html
<div class="pill-list">
  <span class="pill hot">Figma AI</span>  <!-- 강조 항목 -->
  <span class="pill">Protopie</span>      <!-- 일반 항목 -->
</div>
```

- `.pill.hot` — 보라색 계열, 2026년 급증 중인 요구사항에 사용
- `.pill` — 회색 계열, 일반 도구

---

### 5-11. Summary Box

섹션 마무리용 그라디언트 강조 박스.

```html
<div class="summary-box">
  <h3>제목</h3>
  <ul>
    <li>항목 — `→` 화살표가 `::before`로 자동 생성</li>
  </ul>
</div>
```

---

### 5-12. Risk Card Grid

찬반·위험/기회 2열 비교 카드.

```html
<div class="risk-grid">
  <div class="risk-card" style="border-color: rgba(247,107,107,0.3);">
    <h3>위험 영역</h3>
    <ul><li>항목</li></ul>
  </div>
  <div class="risk-card" style="border-color: rgba(86,207,178,0.3);">
    <h3>기회 영역</h3>
    <ul><li>항목</li></ul>
  </div>
</div>
```

- 인라인 `border-color`로 카드 성격을 색상으로 구분
- `ul li::before`에 `—` 대시가 자동 생성

---

## 6. 섹션 구조 패턴

모든 섹션은 동일한 래퍼 패턴을 따른다.

```html
<div class="section">
  <div class="section-label">
    <div class="num">N</div>
    <h2>섹션 제목</h2>
  </div>
  <!-- 본문 컴포넌트들 -->
</div>
```

- `.num`은 `--accent` 색상의 28×28px 라운드 정사각형
- 섹션 번호는 1부터 순차 증가; 새 섹션 추가 시 이후 번호 모두 수정 필요

---

## 7. Hero 구조

```html
<div class="hero">
  <div class="hero-tag">리서치 보고서 · 연도</div>  <!-- 상단 뱃지 -->
  <h1>제목 <span>강조어</span><br>부제목</h1>       <!-- span이 --accent 색 -->
  <p>한 줄 설명</p>
  <div class="hero-meta">
    <div class="hero-meta-item"><strong>키</strong> &nbsp;값</div>
  </div>
</div>
```

- 배경: `linear-gradient(135deg, #1a1430 → #0f1f2e → #111520)`
- `::before` pseudo-element로 보라색 radial glow 효과

---

## 8. Sources 섹션

페이지 최하단 출처 목록. 항상 `.divider` 뒤에 위치.

```html
<div class="divider"></div>
<div class="sources">
  <h4>출처 및 참고 자료</h4>
  <div class="sources-list">
    <a href="URL" target="_blank">기관명 — 문서 제목</a>
  </div>
</div>
```

- 링크 형식: `기관명 — 문서 제목` (긴 URL 그대로 노출 금지)
- 항상 `target="_blank"`

---

## 9. 색상 사용 레퍼런스 요약

```
보라(accent)   → 섹션 번호 / 선택 강조 / hero 태그 / 링크 hover
초록(accent2)  → 긍정 수치 / 수요 높음 뱃지 / 상승 바
주황(accent3)  → 중간 수치 / 경쟁적 뱃지 / 중립 바
빨강(warn)     → 감원 수치 / 치열 뱃지 / 하락 지표
```

---

## 10. 새 컴포넌트 추가 시 원칙

1. 새 CSS는 `</style>` 직전, `/* Responsive */` 블록 앞에 추가
2. 클래스명은 기능 기반 소문자 kebab-case (`skill-level-card`, `port-checklist`)
3. 색상은 반드시 CSS 변수 참조 (`var(--accent)`) — hex 직접 사용 금지
4. 새 카드/패널의 기본 스타일: `background: var(--surface)`, `border: 1px solid var(--border)`, `border-radius: 14px`
5. 인라인 스타일은 컴포넌트 색상 개별 지정 (`--card-color`, `--bar-color`) 등 변수 오버라이드 용도로만 허용
