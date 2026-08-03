# today-market — Stage 1→5 Identity Pipeline Run

**오늘마켓 API 명세서 하나를 입력으로, 개념(Identity)부터 실행 가능한 스킬(Skill)까지의 파생 체인을 자동 도출한 정체성 파이프라인(1→5단계)의 실제 실행 결과 저장소입니다.**

이 저장소는 파이프라인의 **runRoot**(실행별 작업 폴더)이며, 모든 산출물은 아래 5단계를 거쳐 생성되었습니다. 스킬은 사람이 임의로 작성한 파일이 아니라 **체인의 종착점**입니다.

```
Identity ──definesGoal──▶ Goal ──requiresTask──▶ Task ──requiresKnowledge──▶ Knowledge ──appliedThrough──▶ Method ──developsSkill──▶ Skill
(개념)                    (목표)                  (작업)                       (지식/기준)                    (방법/절차)                 (스킬)
```

---

## 파이프라인 구조 (1→5단계)

파이프라인은 3개의 봉인된 멤버가 직렬로 1회씩 실행되는 루프-프리 컴포지트입니다. 반복은 멤버 2/3의 내부 절차에만 존재합니다.

```
[입력: _input 문서 코퍼스 + 동결된 _identity 스냅샷]
        │
        ▼
멤버 1 ─ 진단 HEAD (S1 → S2 → S3 → 4-DIAG)
  S1  후보 추출        문서에서 정체성 후보 추출, C0 로스터(KEEP+MANUAL) 확정
  S2  정체성 분할      후보를 단일 축으로 분할/병합 판정 → C1 출력 세트
  S3  지식 체인 정렬   관계 간선 기반 위상 정렬 → CandidateSetForStage4 로스터
  4-DIAG 표면 진단     시뮬레이션 전용(클로저 미발행), 중복/포함/개념희석 진단
        │                → Stage5HandoffPacket (승인 세트 + 호출 순서)
        ▼  E1 (선택적 diagnose-then-build 게이트: 승인 세트 ⋉ Stage-3 로스터)
멤버 2 ─ candidate_sweep (후보별 4-EXEC 루프, 엄격 직렬·실패 시 중단)
  각 후보를 _identity → _goal → _task → _knowledge → _method → _skill
  6-파일 클로저 체인으로 발행하고 후보별 검증(PASS)으로 봉인
        │
        ▼  E2 (완료 핸드오프: minted-PASS 세트 + 매니페스트 순서)
멤버 3 ─ ledger_culmination (C1 원장 기재 루프 + 완전성 배리어 + C2 1회)
  피드백 원장 작성 → 스테이지별 패치 지시 → 차기 실행 시드 패킷 봉인
        │
        ▼
[종착점: Stage5NextRunSeedPacket + 검증된 RUN 레코드]
```

---

## 이번 실행 결과 (2026-08-03)

- **입력**: [`_input/_document/오늘마켓_API_명세서.md`](_input/_document/) — 문서 1건
- **동결 `_identity` 스냅샷**: 빈 레지스트리 (첫 실행)
- **runID**: `stage1_20260803_todaymarket_purchase_api` (S1 내부 발급)

| 단계 | 결과 | 게이트 |
|---|---|---|
| S1 후보 추출 | 후보 15 → KEEP 7 / MANUAL 3 / DROP 5, C0 로스터 10행 | PASS |
| S2 정체성 분할 | C1 = 10 (KEEP 6 + SPLIT 조각 4), ManualReview 3 | PASS |
| S3 지식 체인 정렬 | CandidateSetForStage4 10행 위상 정렬 | PASS |
| 4-DIAG 표면 진단 | 45쌍 전수 진단, 승인 9/10 (`todaymarket_api_server` 과광범위 부모로 제외) | PASS |
| 멤버 2 스윕 (4-EXEC ×9) | 9/9 minted-PASS — 클로저 파일 54개 + 검증 아티팩트 9개 | PASS |
| 멤버 3 원장 완결 | 원장 9건 기재, 배리어 HELD, C2 1회 — **무변경 시드** (4개 스테이지 전부 NO_FEEDBACK_NEEDED) | PASS |

### 도출된 정체성 9개 (호출 순서)

1. `PRODUCT` — 상품
2. `PURCHASE_REQUEST` — 구매 요청
3. `ERROR_RESPONSE` — 오류 응답
4. `ROOT_PAGE_ENDPOINT` — 웹페이지 제공 엔드포인트
5. `PRODUCT_LIST_ENDPOINT` — 상품 목록 조회 엔드포인트
6. `AMOUNT_VALIDATION` — 금액 검증
7. `PURCHASE_ENDPOINT` — 상품 구매 처리 엔드포인트
8. `PURCHASE_RECORD` — 구매 기록
9. `PURCHASE_HISTORY_ENDPOINT` — 구매 내역 조회 엔드포인트

각 정체성은 `_identity/<NAME>.md`부터 `_skill/<NAME>/SKILL.md`까지 6-파일 클로저 체인을 완결했습니다.
(`todaymarket_api_server`는 4개 엔드포인트 자식을 흡수할 위험이 있어 스킬화에서 제외되고, 경계 재설정 피드백으로 기록되었습니다.)

---

## 폴더 구조

```
today-market\  (= runRoot)
│
│  ◆ 체인 입력
├── _input\
│   └── _document\    파이프라인이 소비하는 문서 코퍼스        오늘마켓_API_명세서.md
│
│  ◆ 파생 체인 (개념당 각 폴더에 파일 1개)
├── _identity\        개념 정의 — 모든 것의 뿌리               <UPPERCASE_CONCEPT>.md
├── _goal\            체인 1단계: 목표                          <concept>_goal.md
├── _task\            체인 2단계: 작업                          <concept>_task.md
├── _knowledge\       체인 3단계: 지식(판정 기준)               <concept>_knowledge.md
├── _method\          체인 4단계: 방법(절차)                    <concept>_method.md
├── _skill\           체인 종착점: 스킬                         <NAME>\SKILL.md
│
│  ◆ 실행 산출물 (파이프라인이 봉인한 아티팩트)
├── _artifact\
│   ├── <stamp>_stage1_..._artifact.md            S1 봉인 아티팩트 (C0 로스터)
│   ├── <stamp>_stage2_..._artifact.md            S2 봉인 아티팩트 (C1)
│   ├── <stamp>_stage3_..._artifact.md            S3 봉인 아티팩트 (Stage-4 로스터)
│   ├── <stamp>_stage4_diag_*.md                  4-DIAG 진단 아티팩트 6종
│   ├── stage4_<n>_<name>_..._artifact.md         후보별 4-EXEC 클로저 검증 (×9)
│   ├── stage4_concept_to_skill_closure_manifest.md   스윕 매니페스트(누산기)
│   ├── stage5_<n>_<name>_..._artifact.md         후보별 피드백 레코드 (×9)
│   ├── stage5_feedback_ledger.md                 피드백 원장
│   ├── stage5_stage{1..4}_patch_instruction.md   스테이지별 패치 지시 (이번 실행: 전부 빈 상태)
│   ├── stage5_next_run_seed_packet.md            차기 실행 시드 패킷 (미소비)
│   └── stage5_run_record.md                      검증된 RUN 레코드
│
│  ◆ 예약 구조 (기계류 자리 — 이번 실행에서는 비어 있음)
├── _entity\          컴포지트 저작 감사 기록 (suite→…→composite 9단계)
└── _deploy\          배포 스테이징 (closure→…→record 6단계)
```

---

## 설계 원칙

1. **개념 없는 폴더는 없다** — 모든 산출물은 `_identity`의 개념 정의로 소급된다.
2. **스킬은 체인의 종착점이다** — Identity→Goal→Task→Knowledge→Method를 전방으로 완성한 뒤에만 스킬이 생성된다.
3. **컴포지트는 루프가 아니다** — 파이프라인 본체는 멤버 3개·엣지 2개의 1회 직렬 실행이며, 모든 반복은 멤버 내부 절차에 산다.
4. **봉인 후 읽기(finalize-then-read)** — 다음 멤버는 이전 멤버의 PASS 게이트로 봉인된 아티팩트만, 섹션 제목으로 위치를 찾아 읽는다.
5. **실패 시 전체 중단** — 어느 멤버든 자기 게이트에 실패하면 이후 엣지는 발화하지 않고 실행 전체가 STOP된다.
6. **시드는 소비하지 않는다** — 차기 실행 시드 패킷의 적용은 다음 실행의 사전 단계 소유이며, 이번 실행 내부에서는 반환 엣지가 존재하지 않는다.
7. **모든 링크는 검증된다** — 체인·로스터·아티팩트 링크는 dangling 0을 유지한다.

## 명명 규칙

- 선행 `_` = **폴더 표식** — 파일명에는 절대 사용하지 않는다
- 정체성 파일은 `_identity/<UPPERCASE>.md`, 체인 파일은 `<concept>_<stage>.md`
- 스킬은 `_skill/<NAME>/SKILL.md`
- 실행 아티팩트는 `<YYYYMMDD_HHMMSS>_<stage>_..._artifact.md` (스탬프는 실행 시각)

---

> 이 저장소는 Common Context Structure(CCS) 볼트 문법 위에서 **stage_1_to_5_identity_pipeline** 컴포지트가 1회 실행된 결과입니다. 다음 실행은 시드 패킷(`_artifact/stage5_next_run_seed_packet.md`)을 읽는 것에서 시작합니다 — 이번 시드는 증거 기반 무변경(NO_FEEDBACK_NEEDED ×4)이므로 기계 수정 없이 그대로 재실행하거나 파이프라인을 종료할 수 있습니다.
