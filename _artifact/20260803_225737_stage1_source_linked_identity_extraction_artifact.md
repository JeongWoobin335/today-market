# Stage 1 Source-Linked Identity Extraction Artifact

- artifactID: 20260803_225737_stage1_source_linked_identity_extraction_artifact
- runID: stage1_20260803_todaymarket_purchase_api
- generatedAt: 2026-08-03 22:57:37 (local)
- producedBy: stage_1_candidate_extraction_skill (sealed composite; RUNTIME Step 0 + E1–E15 serial)
- consumer: Stage 2 (identity fragmentation) — 이 아티팩트 하나만을 유일한 입력으로 읽는다.

---

## SourceManifest

| field | value |
|---|---|
| runID | stage1_20260803_todaymarket_purchase_api |
| admittedAt | 2026-08-03 22:57:37 |
| admissionClass | `_input` (E1: classify/bind, NOT persisted) |
| sourceDocumentPath | `_input/_document/오늘마켓_API_명세서.md` |
| sourceDocumentSha256 | `f9e31632de0292ba8a60408ea72353a46f6777ba4efe583aef3cdeb536b53e6c` |
| documentLineCount | 120 |
| frozenIdentityRegistrySnapshot | `_identity/` (FROZEN, 2026-08-03 시점) — 등록된 기존 정체성 0건 (`.gitkeep`만 존재) |

runID 채굴 근거 (E2, stable_key_construction): 의미 있는 서술자(stage1 + 실행일 + 말뭉치 주제 "오늘마켓 구매 API"), 범위 내 유일성 확인(본 vault에 다른 run 없음), 불변 앵커로 고정, 실행 전 생애주기에 바인딩. 외부에서 공급받지 않고 내부에서 채굴하였다.

## SourceIndex

| sourceID | docType | resolvable link |
|---|---|---|
| SRC-01 | API 명세서 (Markdown) | `_input/_document/오늘마켓_API_명세서.md` |

## SourceDocument

SRC-01의 정제 보존 사본(cleaned copy). 원문 의미 무변경, 전문 보존.

```markdown
# 오늘마켓 구매 API 명세서

> 상품 구매 웹페이지 · 구매 처리 REST API | v1.0 | 2026. 8. 3. | 작성: 정우빈

## 1. 개요

상품(바나나, 우유)을 전시하고 결제를 처리하는 웹페이지와, 상품 구매를 처리하는 REST API입니다.
웹페이지와 API는 하나의 Node.js(Express) 서버가 함께 제공하며, 구매 요청은 상품명·상품갯수·금액·지갑주소 4개 파라미터를 받습니다.

| 항목 | 내용 |
|---|---|
| 기술 스택 | Node.js 22 · Express 5 · CORS 허용 |
| Base URL (배포) | `http://52.79.242.131` |
| Base URL (로컬) | `http://localhost:3000` |
| 데이터 형식 | 요청·응답 모두 JSON (`Content-Type: application/json`) |
| 인증 | 없음 (데모용) · 추후 지갑 서명 검증 연동 예정 |
| 실행 방법 (로컬) | `cd api` → `npm install` → `npm start` |

## 2. 엔드포인트 요약

| 메서드 · 경로 | 설명 |
|---|---|
| `GET /` | 웹페이지(index.html) 제공 |
| `GET /products` | 판매 상품 목록 조회 |
| `POST /purchase` | 상품 구매 처리 **(핵심 API)** |
| `GET /purchases` | 누적 구매 내역 조회 (확인용) |

## 3. 상세 명세

### GET /products — 상품 목록 조회

판매 중인 전체 상품을 배열로 반환합니다. 파라미터 없음.

HTTP 200 응답 예: `[{ "id": 1, "name": "바나나", "price": 3000, "emoji": "🍌", "bg": "#fef9c3" }, { "id": 2, "name": "우유", "price": 2500, "emoji": "🥛", "bg": "#eff6ff" }]`
(`emoji`, `bg`는 웹페이지 표시용 보조 필드)

### POST /purchase — 상품 구매 처리

요청 본문 파라미터 — 4개 모두 필수: `productName`(string, 등록 상품과 일치), `quantity`(integer, 1 이상 정수), `amount`(number, 단가×갯수와 일치), `walletAddress`(string, 구매자 지갑 주소, 블록체인 결제용).

성공 응답(HTTP 200): `{ success: true, message: "구매가 완료되었습니다.", purchase: { orderId, productName, quantity, amount, walletAddress, createdAt } }`

오류 응답 — 모든 오류는 `{ "success": false, "error": "사유" }` 형식:
400 필수 파라미터 누락 / 400 quantity 1 미만 또는 비정수 / 400 amount ≠ 단가×갯수 / 404 등록되지 않은 상품명.

### GET /purchases — 구매 내역 조회

지금까지 처리된 구매 기록 전체를 배열로 반환. 파라미터 없음. 구매 기록은 서버 메모리에 저장되어 서버 재시작 시 초기화.

## 4. 연동 참고 사항

금액 검증(서버가 단가×갯수 재계산), 지갑주소(현재 문자열 기록만, 이후 결제 처리 로직이 server.js에 연결 가능), CORS(모든 출처 허용), 상품 추가(server.js의 products 배열).

## 5. 호출 빠른 시작 (curl)

상품 목록 / 구매 / 구매 내역에 대한 curl 예시 3건 (배포 Base URL 대상).
```

## SourceUnit

전 스팬 무손실 분할 — 11개 유닛의 합집합이 원문 1–120행 전체를 재구성한다 (탈락 스팬 없음, 공백 구분행 포함).

| SourceUnitID | 내용 요약 | sourceLineRanges |
|---|---|---|
| U01 | 문서 제목·메타 (v1.0, 2026-08-03, 작성자 정우빈) | L1–4 |
| U02 | 1. 개요 — 상품 전시/결제 웹페이지 + 구매 REST API, 4개 파라미터, 기술스택·Base URL·JSON·인증 없음(추후 지갑 서명 검증)·실행 방법 표 | L5–18 |
| U03 | 2. 엔드포인트 요약 — GET /, GET /products, POST /purchase(핵심), GET /purchases | L19–27 |
| U04 | 3. GET /products 상세 — 상품 배열(id/name/price/emoji/bg), 표시용 보조 필드 주석 | L28–43 |
| U05 | 3. POST /purchase 파라미터 표 — productName/quantity/amount/walletAddress 4개 모두 필수 + 제약 | L44–54 |
| U06 | 3. POST /purchase 요청 예시 (JSON) | L55–68 |
| U07 | 3. POST /purchase 성공 응답 — purchase 객체(orderId/productName/quantity/amount/walletAddress/createdAt) | L69–85 |
| U08 | 3. 오류 응답 — `{success:false,error}` 고정 형식, 400×3 + 404 조건표 | L86–94 |
| U09 | 3. GET /purchases 상세 — 전체 구매 기록 배열, 메모리 저장·재시작 시 초기화 | L95–99 |
| U10 | 4. 연동 참고 — 금액 검증, 지갑주소 기록·향후 결제 로직 연결, CORS 전체 허용, 상품 추가 방법 | L100–106 |
| U11 | 5. curl 빠른 시작 — 3개 호출 예시 | L107–120 |

커버리지 검증: 1–4, 5–18, 19–27, 28–43, 44–54, 55–68, 69–85, 86–94, 95–99, 100–106, 107–120 — 연속·무결손·무중복.

## SourceProvenance

유닛별 출처 스탬프 — origin path / line range / content hash (유닛 스팬 sha256 앞 16자리; 원문 전체 hash는 SourceManifest.sourceDocumentSha256).

| SourceProvenanceID | SourceUnitID | originPath | lineRange | unitContentHash |
|---|---|---|---|---|
| SP-U01 | U01 | `_input/_document/오늘마켓_API_명세서.md` | L1–4 | `7675fcdd110ee092` |
| SP-U02 | U02 | `_input/_document/오늘마켓_API_명세서.md` | L5–18 | `1512b93ec18b82b9` |
| SP-U03 | U03 | `_input/_document/오늘마켓_API_명세서.md` | L19–27 | `93837236a9537f44` |
| SP-U04 | U04 | `_input/_document/오늘마켓_API_명세서.md` | L28–43 | `03c026166acc522a` |
| SP-U05 | U05 | `_input/_document/오늘마켓_API_명세서.md` | L44–54 | `a63b717ca287e564` |
| SP-U06 | U06 | `_input/_document/오늘마켓_API_명세서.md` | L55–68 | `359b54e48ebc5cf2` |
| SP-U07 | U07 | `_input/_document/오늘마켓_API_명세서.md` | L69–85 | `3c78f9122628e184` |
| SP-U08 | U08 | `_input/_document/오늘마켓_API_명세서.md` | L86–94 | `0fc5060871f2ddb4` |
| SP-U09 | U09 | `_input/_document/오늘마켓_API_명세서.md` | L95–99 | `b2cd17797d27251f` |
| SP-U10 | U10 | `_input/_document/오늘마켓_API_명세서.md` | L100–106 | `0dc61d1dae21db1e` |
| SP-U11 | U11 | `_input/_document/오늘마켓_API_명세서.md` | L107–120 | `4346be2cd99928e5` |

## SourceAlignment

RAW 무채점 링크 — 유닛별로 기존 정체성 연계 여부만 기록. FROZEN 레지스트리가 비어 있으므로 기존 정체성 연계는 전부 불가하며, 전 유닛이 신규 후보 방향(new-candidate) 링크다. 채점 필드는 명시적 미산출 플레이스홀더.

| SourceUnitID | alignment (RAW) | matchConfidence | alignmentType | A(u,r) |
|---|---|---|---|---|
| U01 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U02 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U03 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U04 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U05 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U06 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U07 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U08 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U09 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U10 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| U11 | new-candidate (기존 정체성 없음) | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |

## RequiredForm

이 종류(Stage-1 source-linked identity extraction artifact)의 필수 형태 (E4). 형태만 고정하며 내용값은 고정하지 않는다.

- 필수 섹션(순서 고정): SourceManifest → SourceIndex → SourceDocument → SourceUnit → SourceProvenance → SourceAlignment → RequiredForm → Contract → RequirementAtom → AbsorbedByExistingIdentity → IdentityCandidate → ManualItem → DropItem → C0 Roster → RegistryCollapse → DropLog → counts → ConformanceCheck → VerifiedRunRecord
- 필수 필드: SourceManifest.runID, SourceManifest.sourceDocumentSha256; 모든 후보 행의 4대 source-link 필드 — **SourceDocumentLinks, SourceUnitID/SourceUnitIDs, SourceProvenanceID, sourceLineRanges** (COLLAPSE·DROP 행에도 존속); 각 후보 행의 Stage1Status ∈ {KEEP, MANUAL, COLLAPSE, DROP}와 C0-entry 플래그; COLLAPSE 행의 collapse-target; DROP 행의 drop-reason.
- 선택 섹션: 없음 (전 섹션 mandatory; 내용이 공집합인 섹션은 빈 상태를 명시 기록).
- SCORED 필드 슬롯은 형태상 존재하되 값은 NOT-YET-PRODUCIBLE 플레이스홀더로 표기함이 필수.

## Contract

협력 당사자 간 구속 의무 기록 (E5; E15에서 conformance_check가 표준으로 재독).

| # | party | expects (input) | owes (output) | condition | responsibility boundary |
|---|---|---|---|---|---|
| C-1 | input_admission (E1) | `_input` 말뭉치 | 분류·바인딩된 admitted input (미영속) | 말뭉치 실재 | 영속·검증하지 않음 |
| C-2 | stable_key_construction (E2) | admitted input | 내부 채굴된 불변 runID | E1 완료 | 의미·수명주기 정의 밖 |
| C-3 | source_structuring (E3) | admitted input + runID | 무손실 `_Source` body (Manifest[runID, sourceDocumentSha256]/Index/Document/Unit/Provenance/RAW Alignment), 전 스팬 유닛화 | E2 완료 | 추출·판단하지 않음 |
| C-4 | artifact_form_specification (E4) | — | RequiredForm (필수 섹션·필드) | E3 완료 | 내용값 미고정 |
| C-5 | contract_statement_authoring (E5) | RequiredForm | 본 Contract | E4 완료 | 순서·형태 재진술 금지(참조만) |
| C-6 | corpus_harvesting (E6) | `_Source` 유닛 | 유닛별 source-link 후보 + 전 행에 4대 source-link 필드를 단일 pre-branch 부착점에서 스탬프 | E5 완료 | 개념 여부 판단 밖 |
| C-7 | concept_recognition (E7/E8 분기) | 후보 행 | 행별 정확히 한 arm: 5-A(not-a-candidate) XOR 5-B(candidate) | E6 완료 | 판결·정착 밖 |
| C-8 | claim_grounding (E8, 5-B만) | candidate 행 | 해석 가능한 grounding pointer | 5-B arm | 진위 판단 밖 |
| C-9 | candidate_adjudication (E9, 5-B만) | grounded 후보 + FROZEN 레지스트리 스냅샷 | 정확히 ONE verdict {admit, defer-to-human, reject-as-duplicate} + 근거; 중복/붕괴 판정은 오직 FROZEN 스냅샷 대상 | 5-B arm | 판결 집행 밖 |
| C-10 | disposition_settlement (E7/E10 XOR 병합) | verdict 또는 not-a-candidate | 행별 ONE Stage1Status {KEEP,MANUAL,COLLAPSE,DROP} + C0 플래그 + COLLAPSE target / DROP reason; 4대 source-link 필드 읽기전용 존속 | 한 arm만 발화(대기 없음) | 재판결 금지 |
| C-11 | roster_authoring (E11) | 정착된 전 행 | C0 로스터 = KEEP+MANUAL만, 멤버당 해석 가능한 1행 | E10/E7 병합 완료 | COLLAPSE/DROP 미포함 |
| C-12 | artifact_landing (E12) | 누적 아티팩트 초안 + RegistryCollapse/DropLog/counts 투영 | 영속·확인된 ONE 아티팩트 (착지 전 3개 투영 섹션 기록) | E11 완료 | 제2 아티팩트 금지 |
| C-13 | conformance_check (E13+E15) | 착지 아티팩트 + 본 Contract | 의무 전건 순회 기록 + SourceProvenanceID의 `_Source` 역추적 + PASS/FAIL | E12 완료 | 임의 주장 검증·시스템 감사 밖 |
| C-14 | verified_record (E14, PASS-only) | PASS 판정 | VerifiedRunRecord 봉인 | conformance PASS일 때만; FAIL 시 실패 기록만 남기고 미실행 | 아티팩트 내용 수정 금지 |

구속 조항: 미이행 산출은 침묵 누락이 아니라 계약 위반 실패로 표면화한다. SCORED 필드 수기 조작 금지. Stage 2는 이 아티팩트 하나만 읽는다.

## RequirementAtom

RAW 층 — 말뭉치가 담지한 요구 원자(무채점). SCORED 필드(Q(u)>=theta_req / obligationType / modality)는 명시적 미산출.

| RequirementAtomID | RAW 요구 내용 | SourceUnitIDs | Q(u)>=theta_req | obligationType | modality |
|---|---|---|---|---|---|
| RA-01 | 구매 요청의 4개 파라미터(productName·quantity·amount·walletAddress)는 모두 필수 | U02, U05 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-02 | quantity는 1 이상의 정수여야 함 | U05, U08 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-03 | amount는 단가×갯수와 일치해야 하며 서버가 재계산 검증 | U05, U08, U10 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-04 | productName은 등록된 상품과 일치해야 함 (불일치 시 404) | U05, U08 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-05 | 모든 오류 응답은 `{success:false, error}` 고정 형식 | U08 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-06 | 요청·응답은 모두 JSON (`Content-Type: application/json`) | U02 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |
| RA-07 | 구매 기록은 서버 메모리 저장 — 재시작 시 초기화 | U09 | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE | NOT-YET-PRODUCIBLE |

## AbsorbedByExistingIdentity

SCORED 슬롯 — NOT-YET-PRODUCIBLE. (부가 사실: FROZEN `_identity` 레지스트리 스냅샷이 공집합이므로 이번 run에서 기존 정체성으로의 흡수 후보 자체가 성립하지 않음. 값 산출은 후속 단계 소관.)

## IdentityCandidate

E6에서 수확된 전 후보 15행. 4대 source-link 필드는 단일 pre-branch 부착점(E6)에서 전 행에 스탬프되어 COLLAPSE·DROP 포함 전 행에 읽기전용 존속. 각 행은 E7 XOR에서 정확히 한 arm을 탔다. SCORED 필드 IC(c)>=theta_identity = NOT-YET-PRODUCIBLE (전 행 공통).

| CandID | 후보 개념 (noun name) | 구조적 역할 근거 | arm | verdict (E9) / pre-reject (E7) | groundedBy (E8) | Stage1Status | C0 | SourceDocumentLinks | SourceUnitIDs | SourceProvenanceID | sourceLineRanges |
|---|---|---|---|---|---|---|---|---|---|---|---|
| CAND-01 | 상품 (Product) | id/name/price/emoji/bg 필드를 가진 엔티티; 목록 조회·구매 대상의 축 | 5-B | admit — 명세 전반이 이 엔티티를 중심으로 구조화됨 | `_input/_document/오늘마켓_API_명세서.md#L28-43` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U02, U04 | SP-U02, SP-U04 | L5–18, L28–43 |
| CAND-02 | 구매 요청 (PurchaseRequest) | 4개 필수 파라미터로 고정된 요청 단위; 핵심 API의 입력 형태 | 5-B | admit — 파라미터 표·예시·오류 조건이 이 단위를 규정 | `_input/_document/오늘마켓_API_명세서.md#L44-68` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U02, U05, U06 | SP-U02, SP-U05, SP-U06 | L5–18, L44–54, L55–68 |
| CAND-03 | 구매 기록 (PurchaseRecord) | orderId~createdAt 필드의 영속 단위; /purchases가 반환하는 축적 대상 | 5-B | admit — 성공 응답과 조회 엔드포인트가 이 단위로 구조화 | `_input/_document/오늘마켓_API_명세서.md#L69-85` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U07, U09 | SP-U07, SP-U09 | L69–85, L95–99 |
| CAND-04 | 오류 응답 (ErrorResponse) | `{success:false,error}` 고정 형식 + 상태코드 조건표라는 독자 형태 | 5-B | admit — 명세가 전 오류를 이 한 형식으로 묶음 | `_input/_document/오늘마켓_API_명세서.md#L86-94` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U08 | SP-U08 | L86–94 |
| CAND-05 | 구매 API 엔드포인트 (PurchaseApiEndpoint) | 메서드·경로·설명으로 색인되는 4개 진입점 구조 | 5-B | admit — 요약표와 상세 명세의 조직 축 | `_input/_document/오늘마켓_API_명세서.md#L19-27` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U03, U04, U05, U08, U09 | SP-U03, SP-U04, SP-U05, SP-U08, SP-U09 | L19–27, L28–43, L44–54, L86–94, L95–99 |
| CAND-06 | 금액 검증 (AmountValidation) | 서버측 단가×갯수 재계산 규칙; 400 오류 조건과 연동 참고에 반복 등장 | 5-B | admit — 독자적 검증 규칙으로 구조적 역할 수행 | `_input/_document/오늘마켓_API_명세서.md#L100-106` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U05, U08, U10 | SP-U05, SP-U08, SP-U10 | L44–54, L86–94, L100–106 |
| CAND-07 | 오늘마켓 API 서버 (TodayMarketApiServer) | 웹페이지+API를 함께 제공하는 단일 Node.js(Express) 서버; 명세 대상 시스템 자체 | 5-B | admit — 문서 전체가 이 시스템의 정체를 규정 | `_input/_document/오늘마켓_API_명세서.md#L5-18` | KEEP | yes | `_input/_document/오늘마켓_API_명세서.md` | U01, U02, U10 | SP-U01, SP-U02, SP-U10 | L1–4, L5–18, L100–106 |
| CAND-08 | 지갑 주소 (WalletAddress) | 블록체인 결제용 구매자 식별 문자열; 현재는 기록만, 향후 결제 로직 연결 예정 | 5-B | defer-to-human — 독립 정체성인지 PurchaseRequest의 필드에 그치는지 경계선; 장래 역할이 미확정 | `_input/_document/오늘마켓_API_명세서.md#L100-106` | MANUAL | yes | `_input/_document/오늘마켓_API_명세서.md` | U05, U06, U10 | SP-U05, SP-U06, SP-U10 | L44–54, L55–68, L100–106 |
| CAND-09 | 인증 (Authentication) | 현재 없음(데모) · 추후 지갑 서명 검증 연동 예정으로 명세에 자리만 존재 | 5-B | defer-to-human — 현존 구조가 아닌 예고된 구조; 증거가 admit도 duplicate도 아님 | `_input/_document/오늘마켓_API_명세서.md#L5-18` | MANUAL | yes | `_input/_document/오늘마켓_API_명세서.md` | U02, U10 | SP-U02, SP-U10 | L5–18, L100–106 |
| CAND-10 | 상품 구매 웹페이지 (PurchaseWebPage) | GET /가 제공하는 index.html; 상품 전시·결제 UI | 5-B | defer-to-human — API 명세 범위 내 독립 정체성인지 부속 산출물인지 경계선 | `_input/_document/오늘마켓_API_명세서.md#L19-27` | MANUAL | yes | `_input/_document/오늘마켓_API_명세서.md` | U01, U02, U03 | SP-U01, SP-U02, SP-U03 | L1–4, L5–18, L19–27 |
| CAND-11 | 바나나 | 상품의 개별 인스턴스; 예시 데이터로만 등장 | 5-A | not-a-candidate — worked example 내 인스턴스 (harvest noise 규칙) | — (5-A는 grounding 미부착) | DROP | no | `_input/_document/오늘마켓_API_명세서.md` | U02, U04, U06 | SP-U02, SP-U04, SP-U06 | L5–18, L28–43, L55–68 |
| CAND-12 | 우유 | 상품의 개별 인스턴스; 예시 데이터로만 등장 | 5-A | not-a-candidate — worked example 내 인스턴스 | — | DROP | no | `_input/_document/오늘마켓_API_명세서.md` | U02, U04 | SP-U02, SP-U04 | L5–18, L28–43 |
| CAND-13 | CORS | 범용 기술 용어; 설정값 언급에 그침 | 5-A | not-a-candidate — bare generic word (도메인의 명명 단위 아님) | — | DROP | no | `_input/_document/오늘마켓_API_명세서.md` | U02, U10 | SP-U02, SP-U10 | L5–18, L100–106 |
| CAND-14 | Base URL | 배포/로컬 설정값; 구조가 아닌 값 | 5-A | not-a-candidate — 설정값 (formula/config noise) | — | DROP | no | `_input/_document/오늘마켓_API_명세서.md` | U02 | SP-U02 | L5–18 |
| CAND-15 | curl 빠른 시작 | 호출 절차 예시 묶음의 라벨 | 5-A | not-a-candidate — procedure/step label (harvest noise 규칙) | — | DROP | no | `_input/_document/오늘마켓_API_명세서.md` | U11 | SP-U11 | L107–120 |

## ManualItem

| CandID | 후보 | 사람 검토가 필요한 이유 |
|---|---|---|
| CAND-08 | 지갑 주소 (WalletAddress) | 필드 vs 독립 정체성 경계선 + 향후 블록체인 결제 연동 시 역할 확장 예고 (U10) |
| CAND-09 | 인증 (Authentication) | 현재 부재·장래 예고된 구조 — 정체성 선언 시점 판단 필요 (U02, U10) |
| CAND-10 | 상품 구매 웹페이지 (PurchaseWebPage) | API 명세 도메인 내 독립 정체성 여부 판단 필요 (U01–U03) |

## DropItem

| CandID | 후보 | drop-reason | SourceDocumentLinks | SourceUnitIDs | SourceProvenanceID | sourceLineRanges |
|---|---|---|---|---|---|---|
| CAND-11 | 바나나 | worked example 내 인스턴스 | `_input/_document/오늘마켓_API_명세서.md` | U02, U04, U06 | SP-U02, SP-U04, SP-U06 | L5–18, L28–43, L55–68 |
| CAND-12 | 우유 | worked example 내 인스턴스 | `_input/_document/오늘마켓_API_명세서.md` | U02, U04 | SP-U02, SP-U04 | L5–18, L28–43 |
| CAND-13 | CORS | bare generic word (범용 기술 용어) | `_input/_document/오늘마켓_API_명세서.md` | U02, U10 | SP-U02, SP-U10 | L5–18, L100–106 |
| CAND-14 | Base URL | 설정값 — 구조적 명명 단위 아님 | `_input/_document/오늘마켓_API_명세서.md` | U02 | SP-U02 | L5–18 |
| CAND-15 | curl 빠른 시작 | procedure/step label | `_input/_document/오늘마켓_API_명세서.md` | U11 | SP-U11 | L107–120 |

## C0 Roster

C0 = KEEP + MANUAL만, 멤버당 해석 가능한 1행 (what / where / role). COLLAPSE·DROP 미포함. 전 행이 본 아티팩트의 IdentityCandidate 행과 `_Source` 유닛으로 해석된다.

| C0# | CandID | what (후보 개념) | Stage1Status | where (resolves to) | role |
|---|---|---|---|---|---|
| C0-01 | CAND-01 | 상품 (Product) | KEEP | IdentityCandidate CAND-01 → SP-U02, SP-U04 (`_input/_document/오늘마켓_API_명세서.md` L5–18, L28–43) | 전시·구매 대상 엔티티 |
| C0-02 | CAND-02 | 구매 요청 (PurchaseRequest) | KEEP | IdentityCandidate CAND-02 → SP-U02, SP-U05, SP-U06 (L5–18, L44–54, L55–68) | 핵심 API의 4-파라미터 입력 단위 |
| C0-03 | CAND-03 | 구매 기록 (PurchaseRecord) | KEEP | IdentityCandidate CAND-03 → SP-U07, SP-U09 (L69–85, L95–99) | 구매 처리 결과의 영속(메모리) 단위 |
| C0-04 | CAND-04 | 오류 응답 (ErrorResponse) | KEEP | IdentityCandidate CAND-04 → SP-U08 (L86–94) | 전 오류의 고정 응답 형식 |
| C0-05 | CAND-05 | 구매 API 엔드포인트 (PurchaseApiEndpoint) | KEEP | IdentityCandidate CAND-05 → SP-U03 외 (L19–27 등) | 4개 진입점의 조직 축 |
| C0-06 | CAND-06 | 금액 검증 (AmountValidation) | KEEP | IdentityCandidate CAND-06 → SP-U05, SP-U08, SP-U10 (L44–54, L86–94, L100–106) | 서버측 단가×갯수 재계산 규칙 |
| C0-07 | CAND-07 | 오늘마켓 API 서버 (TodayMarketApiServer) | KEEP | IdentityCandidate CAND-07 → SP-U01, SP-U02, SP-U10 (L1–4, L5–18, L100–106) | 명세 대상 시스템 |
| C0-08 | CAND-08 | 지갑 주소 (WalletAddress) | MANUAL | IdentityCandidate CAND-08 → SP-U05, SP-U06, SP-U10 (L44–54, L55–68, L100–106) | 블록체인 결제용 구매자 식별 (검토 대기) |
| C0-09 | CAND-09 | 인증 (Authentication) | MANUAL | IdentityCandidate CAND-09 → SP-U02, SP-U10 (L5–18, L100–106) | 예고된 지갑 서명 검증 구조 (검토 대기) |
| C0-10 | CAND-10 | 상품 구매 웹페이지 (PurchaseWebPage) | MANUAL | IdentityCandidate CAND-10 → SP-U01, SP-U02, SP-U03 (L1–4, L5–18, L19–27) | 상품 전시·결제 UI (검토 대기) |

## RegistryCollapse

COLLAPSE 판정 후보: 없음 (0건).

FROZEN `_identity` 레지스트리 스냅샷이 공집합(등록 정체성 0건)이므로 candidate_adjudication(E9)의 중복 검사에서 reject-as-duplicate가 성립할 대상이 존재하지 않았다. 따라서 이번 run의 COLLAPSE는 구조적으로 0건이다.

| CandID | 후보 | collapse-target | SourceDocumentLinks | SourceUnitIDs | SourceProvenanceID | sourceLineRanges |
|---|---|---|---|---|---|---|
| — | (해당 없음) | — | — | — | — | — |

## DropLog

DROP 5건 — 전 행에 4대 source-link 필드 존속 (상세는 DropItem 섹션과 동일 근거).

| CandID | 후보 | drop-reason | sourceLineRanges |
|---|---|---|---|
| CAND-11 | 바나나 | worked example 내 인스턴스 | L5–18, L28–43, L55–68 |
| CAND-12 | 우유 | worked example 내 인스턴스 | L5–18, L28–43 |
| CAND-13 | CORS | bare generic word | L5–18, L100–106 |
| CAND-14 | Base URL | 설정값 | L5–18 |
| CAND-15 | curl 빠른 시작 | procedure label | L107–120 |

## counts

| metric | count |
|---|---|
| totalCandidates | 15 |
| KEEP | 7 |
| MANUAL | 3 |
| COLLAPSE | 0 |
| DROP | 5 |
| C0 roster members (KEEP+MANUAL) | 10 |
| SourceUnits | 11 |
| RequirementAtoms (RAW) | 7 |
| admitted source documents | 1 |

검산: 7 + 3 + 0 + 5 = 15 = totalCandidates. C0 = 7 + 3 = 10. 전 후보가 정확히 하나의 Stage1Status를 가짐 (미정착 0, 이중 상태 0).

## ConformanceCheck

Contract(E5)를 표준으로 착지된 본 아티팩트를 의무 전건 순회 (E13 + E15). 판정 근거를 개별 기록하며 어떤 위반도 묵과하지 않는다.

| # | obligation | 판정 | 근거 |
|---|---|---|---|
| 1 | C-1: `_input` 분류·바인딩, 미영속 | conforms | SourceManifest.admissionClass 기록; `_input` 원본 외 별도 영속 사본 없음 |
| 2 | C-2: runID 내부 채굴·불변 | conforms | SourceManifest.runID = stage1_20260803_todaymarket_purchase_api; 채굴 근거 4규칙 기록 |
| 3 | C-3: 무손실 `_Source` body + sourceDocumentSha256 | conforms | 11개 유닛 합집합 = L1–120 전체 (연속·무결손); Manifest에 sha256 기록; 유닛별 provenance 전건 존재 |
| 4 | C-4: RequiredForm 고정 | conforms | RequiredForm 섹션에 필수 섹션·필드 명시 |
| 5 | C-5: 구속 Contract 존재, 전 당사자 명명 | conforms | Contract 섹션 C-1~C-14, 당사자별 input/output/condition/boundary 완비 |
| 6 | C-6: 4대 source-link 필드를 전 후보 행에 스탬프 (DROP·COLLAPSE 포함) | conforms | IdentityCandidate 15행 전건 + DropItem/DropLog에 4대 필드 존속; COLLAPSE는 0건(빈 상태 명시) |
| 7 | C-7: 행별 XOR — 정확히 한 arm | conforms | 15행 전건 arm 표기: 5-B 10행, 5-A 5행; 양 arm 중복 0 |
| 8 | C-8: 5-B 행에 grounding pointer 부착·해석 가능 | conforms | 5-B 10행 전건 groundedBy 경로+행범위 포인터; 원문 해당 행에서 열람 가능 확인 |
| 9 | C-9: FROZEN 스냅샷 대상 ONE verdict | conforms | 5-B 행별 단일 verdict + 근거; 중복 판정은 공집합 스냅샷 기준 (성립 대상 없음) |
| 10 | C-10: 행별 ONE Stage1Status + C0 플래그 + COLLAPSE target/DROP reason | conforms | 15행 전건 단일 status; DROP 5행 reason 기록; COLLAPSE 0건이므로 target 해당 없음 |
| 11 | C-11: C0 로스터 = KEEP+MANUAL만, 해석 가능한 1행/멤버 | conforms | C0 Roster 10행 = KEEP 7 + MANUAL 3; 행별 what/where/role 완비, where가 실재 행·유닛으로 해석 |
| 12 | C-12: ONE 아티팩트 착지, 착지 전 RegistryCollapse/DropLog/counts 투영 | conforms | 본 파일 단일 아티팩트; 3개 투영 섹션 포함 상태로 착지·재독 확인 |
| 13 | C-13: SourceProvenanceID `_Source` 역추적 | conforms | 표본 전수 추적: C0 전 행의 SourceProvenanceID(SP-U01~SP-U11)가 SourceProvenance 표의 실재 행으로 해석되고, 각 행의 originPath+lineRange가 admitted 원문(sha256 `f9e3...b53e6c`)의 실제 스팬과 unitContentHash로 일치 |
| 14 | SCORED 필드 미조작 | conforms | SourceAlignment/RequirementAtom/AbsorbedByExistingIdentity/IC(c)의 SCORED 슬롯 전건 NOT-YET-PRODUCIBLE 플레이스홀더 — 수기 값 0건 |
| 15 | counts 정합 | conforms | 7+3+0+5=15; C0=10 검산 일치 |

**결과: PASS** — 전 의무 충족, 비순응 0건.

## VerifiedRunRecord

E14 PASS-only 게이트 통과 (ConformanceCheck = PASS) → verified_record 실행·봉인.

```text
skill-use event: stage_1_candidate_extraction_skill 실행 1회
  (runID stage1_20260803_todaymarket_purchase_api, 2026-08-03 22:57:37)

record: 위 skill-use가 본 아티팩트를 산출했다는 기록 (captured, finalized once)

named outcome (Group A):
  kind -> Stage-1 settled source-linked timestamped extraction artifact
  name -> 20260803_225737_stage1_source_linked_identity_extraction_artifact

claim: "말뭉치 1문서에서 15개 후보를 수확·정착(KEEP 7 / MANUAL 3 / COLLAPSE 0 / DROP 5)하고
  C0 로스터 10행을 저술하여 단일 아티팩트로 착지, conformance PASS를 받았다"

groundedBy (Group B, ground) ->
  _artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md
  (본 파일; ConformanceCheck 섹션 + SourceProvenance 표가 검사 가능한 근거)

verification (Group B, verify): 포인터를 따라 착지 아티팩트를 재독 —
  필수 섹션 전건 존재, counts 검산 일치, provenance 해석 일치, PASS 기록 실재
  verdict -> VERIFIED

converged verified record: named outcome + grounded-and-verified claim이
  이 단일 레코드로 수렴. SEALED.
```

seal: **SEALED on conformance PASS** — Stage 2는 이 아티팩트만을 유일한 입력으로 읽는다.
