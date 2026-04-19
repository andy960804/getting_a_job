# Career-Harness v1.0

## 프로젝트 목적
3C4P 기반 경험 정리 및 AI 탐지 회피형 자소서 작성을 통한 취업 성공.

## 전략 원칙 (자소서 바이블 — 면접왕 이형)

### 취업 준비 우선순위
- **직무 60%** / **산업 20%** / **직장 20%**

### 자소서의 본질
- **비즈니스 문서** — 요약·압축이 핵심. 논술·작문 시험이 아니다.
- **면접의 요약본** — 면접관이 꼬리 질문할 소재를 심는 문서.
- **역기획 원칙** — 받고 싶은 면접 질문을 먼저 정하고 자소서를 설계한다.

### 광탈 방지 원칙
- 스펙 나열 금지 — 실무역량과 연결된 경험 정리에 집중
- 필살기 경험 3개로 모든 문항 대응 (각도를 바꿔 재활용)
- 글쓰기 스킬보다 경험의 해석 역량이 합격을 결정한다

## 3C4P 프레임워크
> 정의 상세: `rules/skills/archivist/card_format.md` 참조
- **3C (Why)**: Customer → Company → Competitor
- **4P (What/How)**: Product → Place → Price → Promotion
- **서술 순서**: WHAT(P1) → WHY(3C) → HOW(P2·P3·P4) → 인사이트

## 디렉터리 구조
```
getting_a_job/
├── CLAUDE.md                        ← 이 파일 (프로젝트 지도)
├── rules/
│   ├── analyst.md                   ← Agent 1: 공고 분석 & 매칭 전략
│   ├── archivist.md                 ← Agent 2: 3C4P 경험 구조화 & DB 관리
│   ├── ghostwriter.md               ← Agent 3: 자소서 집필 & AI 탐지 회피
│   └── skills/                      ← 에이전트별 온디맨드 스킬 파일
└── db/
    ├── cv.md                        ← 마스터 CV (단일 소스)
    ├── tracker.tsv                  ← 지원 현황 트래커 (TSV, 중복 방지)
    ├── experience_db.md             ← 경험 카드 인덱스 + 역량 매핑표
    ├── applications_log.md          ← 지원 상세 로그 + 면접 일정 + 주간 KPI
    ├── profiles/target_profile.yaml ← 목표 직무·연봉·지역 설정
    ├── experiences/                 ← 경험 카드 (YYYYMMDD_경험명.md)
    ├── jd_analysis/                 ← 공고 분석본 (회사명_직무.md)
    └── drafts/                      ← 자소서 초안 (회사명_직무_v버전.md)
```

## 워크플로우
- **루트 A (JD-First)**: 공고 입력 → analyst → archivist → ghostwriter(v1→v2→v3) → 제출
- **루트 B (Experience-First)**: 경험 입력 → archivist(3C4P Linter) → DB 저장 → 루트 A 합류

파일 저장 규칙: experiences=`YYYYMMDD_경험명.md` / drafts=`회사명_직무_v버전.md` / jd=`회사명_직무.md`

## 자가학습 루프
실수 감지(사용자 정정 / 게이트 반복 실패 / 파일 불일치) 시 Claude가 자동 실행:
```
db/error_log.md 기록 → rules/lessons_learned.md 규칙 추가 → 에이전트 Learned Constraints 동기화
동일 실수 2회 이상 → Hard Constraints로 격상
```

## 품질 기준
- AI 탐지: 인간 작성 확률 80% 이상
- 경험 카드: 3C+4P 7개 레이어 모두 PASS
- 핵심 철학: 결과 수치 < 행동의 사고 과정
- 공고 분석: 역량 Top 5 + 컬처핏 Top 3 + 지뢰 목록
- 자소서 최종본(v3): Anti-AI 체크리스트 15항 전체 통과
