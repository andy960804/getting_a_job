# Career-Harness v1.0

## 프로젝트 목적
3C4P 기반 경험 정리 및 AI 탐지 회피형 자소서 작성을 통한 취업 성공.

## 전략 원칙 (자소서 바이블 — 면접왕 이형)

### 취업 준비 우선순위
- **직무 60%** — 나의 강점이 발휘되는 실무 역량 중심
- **산업 20%** — 관심사 & 시장 트렌드 파악
- **직장 20%** — 커리어 성장 관점

### 자소서의 본질
- **자소서 = 비즈니스 문서** — 논술·작문 시험이 아니다. 요약과 압축이 핵심
- **자소서 = 면접의 요약본** — 면접관이 꼬리 질문할 수 있는 소재를 심는 문서
- **역기획 원칙** — 면접에서 어떤 질문을 받고 싶은가를 먼저 정하고, 자소서를 그 방향으로 설계한다

### 광탈 방지 원칙
- 스펙 나열 금지 — 실무역량과 연결된 경험 정리에 집중
- 필살기 경험 3개로 모든 문항에 대응 (경험을 각도를 바꿔 재활용)
- 글쓰기 스킬보다 경험의 해석 역량이 합격을 결정한다

## 3C4P 프레임워크
마케팅의 3C 분석 + 4P 믹스를 자소서 경험 서술에 적용한 구조.
**핵심 철학: 결과 수치보다 행동의 사고 과정이 중요하다.**

### 3C — Why (왜 이 일을 했는가)
- **C1 Customer** — 혜택을 받는 대상 / 그들이 필요로 한 것
- **C2 Company** — 본인이 속한 조직·팀의 목표, 문제 또는 기회 / 팀 내 본인의 역할
- **C3 Competitor** — 조사한 대상(경쟁사·타 팀·선행 사례) / 조사 후 적용한 내용

### 4P — What & How (무엇을·어떻게 했는가)
- **P1 Product** — 도출된 결과물 / 그 결과의 의미
- **P2 Place** — 문제 해결점을 발견한 지점 / 실행 위치와 채널
- **P3 Price** — 비용 절감 또는 시간 단축 효과
- **P4 Promotion** — 알리기 관점(설명·공유·설득) / 고객 니즈 반영 방식

### 자소서 적용 구조
```
WHAT  → P1(Product) 중심으로 결과를 먼저 제시
WHY   → C1+C2+C3로 맥락과 판단 근거를 설명
HOW   → P2+P3+P4로 실행 방식과 효과를 풀어냄
마무리 → 사고 과정에서 얻은 인사이트 1–2줄
```

## 디렉터리 구조
```
getting_a_job/
├── CLAUDE.md                        ← 이 파일 (프로젝트 지도)
├── rules/
│   ├── analyst.md                   ← Agent 1: 공고 분석 & 매칭 전략
│   ├── archivist.md                 ← Agent 2: 3C4P 경험 구조화 & DB 관리 (Linter 포함)
│   └── ghostwriter.md               ← Agent 3: 자소서 집필 & AI 탐지 회피 (15항 체크리스트)
└── db/
    ├── cv.md                        ← 마스터 CV (단일 소스)
    ├── tracker.tsv                  ← 지원 현황 트래커 (TSV, 중복 방지)
    ├── experience_db.md             ← 경험 카드 인덱스 + 역량 매핑표
    ├── applications_log.md          ← 지원 상세 로그 + 면접 일정 + 주간 KPI
    ├── profiles/
    │   └── target_profile.yaml      ← 목표 직무·연봉·지역 설정
    ├── experiences/                 ← 경험 카드 (YYYYMMDD_경험명.md)
    ├── jd_analysis/                 ← 공고 분석본 (회사명_직무.md)
    └── drafts/                      ← 자소서 초안 (회사명_직무_v버전.md)
```

## 워크플로우

### 루트 A — 공고 먼저 (JD-First)
```
[공고 URL 또는 텍스트 입력]
    ↓
analyst     → 역량맵 Top5 + 컬처핏 Top3 + 지뢰목록 → db/jd_analysis/ 저장
    ↓           (GATE: Top5 미완성 시 다음 단계 차단)
archivist   → 경험 DB 매칭 탐색 / 신규 경험이면 3C4P Linter 실행
    ↓           (Linter: 7레이어 PASS 必 → db/experiences/ 저장 → experience_db.md 업데이트)
ghostwriter → v1 초안
              → [비즈니스 레터 체크 7항] → v2 리라이팅
              → [Anti-AI 체크 15항] → v3 최종본
              → [최종 제출 전 점검 7항] → 제출
[db/drafts/ 저장 + tracker.tsv + applications_log.md 업데이트]
```

### 루트 B — 경험 먼저 (Experience-First)
```
[경험 서술 입력]
    ↓
archivist   → 3C4P Linter (7레이어 검사 → FAIL 시 추가 질문 → PASS 후 저장)
    ↓
experience_db.md 업데이트 (인덱스 + 역량 매핑)
    ↓
[공고 입력 대기 → 루트 A의 archivist 단계로 합류]
```

## 에이전트 호출 규칙
- 각 단계는 해당 `rules/*.md`를 컨텍스트로 로드한 뒤 진행한다.
- 경험 카드: `db/experiences/YYYYMMDD_경험명.md` + `db/experience_db.md` 인덱스 동시 업데이트
- 자소서 초안: `db/drafts/회사명_직무_v버전.md`
- 공고 분석본: `db/jd_analysis/회사명_직무.md`
- 지원 기록: `db/tracker.tsv` + `db/applications_log.md` 동시 업데이트

## 자가학습 루프 (Self-Improving Harness)

프로젝트 진행 중 실수가 발생하면 Claude가 **즉시 자동**으로 아래를 수행한다.
사용자가 별도로 요청하지 않아도 실행된다.

```
실수 감지
  (사용자 정정 / 게이트 반복 실패 / 파일 불일치 / 명시적 지적)
    ↓
db/error_log.md 에 구조화 기록
    ↓
rules/lessons_learned.md 해당 에이전트 섹션에 규칙 추가
    ↓
해당 에이전트 파일의 Learned Constraints 섹션 동기화
    ↓
동일 실수 2회 이상 → Hard Constraints로 격상
```

**감지 트리거:**
- 사용자가 "틀렸다", "다시 해줘", "아니야" 등으로 정정할 때
- 동일 Linter 항목이 2회 연속 FAIL할 때
- 파일명·포맷이 규칙과 불일치할 때

## 품질 기준
- 자소서 문항당 AI 탐지 점수 목표: 인간 작성 확률 80% 이상
- 경험 카드 1건당 3C(Customer/Company/Competitor) + 4P(Product/Place/Price/Promotion) 7개 레이어 모두 PASS
- 핵심 철학 준수: 결과 수치 < 행동의 사고 과정 (Why → What → How 순서로 서술)
- 공고 분석 리포트: 핵심 역량 Top 5 + 컬처핏 키워드 Top 3 + 지뢰 목록 포함
- 자소서 최종본(v3): Anti-AI 리라이팅 체크리스트 15항 전체 통과
