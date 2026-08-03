# Stage 2 Identity Fragmentation Artifact

- artifactID: 20260803_230223_stage2_identity_fragmentation_artifact
- canonicalBasename: stage2_identity_fragmentation_artifact.md (run-scope 토큰 `20260803_230223_` 접두 — 공유 `_artifact/` 루트 누적 규약)
- generatedAt: 2026-08-03 23:02:23 (local)
- producedBy: stage_2_identity_fragmentation_skill (sealed composite; E1–E15 serial, ONE owning context)
- input: `_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md` (유일한 외부 입력; SEALED Stage-1 아티팩트)
- consumer: Stage 3 — 이 아티팩트 하나만을 읽는다.

---

## InputAdmission

E1 (input_admission): Stage-1 봉인 아티팩트에서 입력 후보 집합을 admit — 분류·바인딩만 수행, 영속하지 않음.

- C0 = FinalIdentityCandidate(KEEP 7) ∪ ManualReviewCandidate(MANUAL 3) = **10건** — Stage-1 `## C0 Roster` 섹션의 C0-01~C0-10 전 행.
- `derivedFromStage1CandidateID` = admit된 Stage-1 후보 id (CAND-01 ~ CAND-10) — Stage-1 계보로 각 행에 바인딩.
- **RegistryCollapse**: Stage-1 `## RegistryCollapse` 섹션 확인 결과 **0건** (FROZEN `_identity` 레지스트리가 공집합이어서 COLLAPSE가 구조적으로 성립하지 않았음). 별도의 preserve-only `ExistingIdentityReferenceSet` 채널로 admit — **판결 흐름에 진입하지 않으며 어떤 fragmentation verdict도 받지 않는다** (공집합 상태를 명시 기록).
- C0 외 어떤 행도 승격·재구성하지 않음 (COLLAPSE 0건, DROP 5건은 admit 대상 아님).

| admitted set | 구성 | 건수 |
|---|---|---|
| C0 | CAND-01~07 (KEEP) + CAND-08~10 (MANUAL) | 10 |
| ExistingIdentityReferenceSet (preserve-only) | RegistryCollapse 참조 | 0 |

## StableKeys

E2 (stable_key_construction): 각 admit 행에 안정 키 `Stage2CandidateID`와 경로 라벨형 `NormalizedName`을 채굴. Split 파편에는 부모 키 파생형 접미(a–d)를 부여해 범위 내 유일성을 확보.

| Stage2CandidateID | derivedFromStage1CandidateID | NormalizedName |
|---|---|---|
| S2C-01 | CAND-01 | product |
| S2C-02 | CAND-02 | purchase_request |
| S2C-03 | CAND-03 | purchase_record |
| S2C-04 | CAND-04 | error_response |
| S2C-05 | CAND-05 | purchase_api_endpoint |
| S2C-05a | CAND-05 | root_page_endpoint |
| S2C-05b | CAND-05 | product_list_endpoint |
| S2C-05c | CAND-05 | purchase_endpoint |
| S2C-05d | CAND-05 | purchase_history_endpoint |
| S2C-06 | CAND-06 | amount_validation |
| S2C-07 | CAND-07 | todaymarket_api_server |
| S2C-08 | CAND-08 | wallet_address |
| S2C-09 | CAND-09 | authentication |
| S2C-10 | CAND-10 | purchase_web_page |

(S2C-05a~d는 E6/E7 분해 확정 후 이 표에 소급 기재된 것이 아니라, 단일 누적 아티팩트 원칙에 따라 파편 생성 시점에 E2의 채굴 규칙으로 발급된 키를 본 섹션이 수용한 것이다. 키 발급 규칙 자체는 E2가 고정했다.)

## RequiredForm

E3 (artifact_form_specification): 본 종류(Stage-2 identity fragmentation artifact)의 필수 형태. 형태만 고정, 내용값은 고정하지 않는다.

- 필수 섹션(순서 고정): InputAdmission → StableKeys → RequiredForm → Contract → ClaimGrounding → SingleAxisSeparation → LateralPartition → ConceptRelationshipMap → FragmentationAdjudication → FragmentationSettlement → C1 → ManualReviewSet → ExistingIdentityReferenceSet → ArtifactLanding → LinkClosureCheck → InterlockCheck → ConformanceCheck → VerifiedRunRecord
- 필수 필드 (9 codex-required, 행 단위): **Stage2CandidateID, derivedFromStage1CandidateID, fragmentationAction, fragmentedFrom, collapsedFrom, FinalIdentityNAME, NormalizedName, ProvenanceLinkToStage1, Stage2Status**
- 보조 필드 (auxiliary, conformance 하드게이트 제외): FragmentationDecisionReason
- 내용이 공집합인 섹션은 빈 상태를 명시 기록 (ExistingIdentityReferenceSet 해당).

## Contract

E4 (contract_statement_authoring): 집행 가능한 conformance 계약.

| # | 조항 |
|---|---|
| K-1 | C0 후보만 fragmentation verdict를 받는다; RegistryCollapse/ExistingIdentityReferenceSet은 판결 흐름에 절대 진입하지 않는다. |
| K-2 | 각 C0 후보는 정확히 하나의 verdict {Keep, Split, Merge, Reject, ManualReview}를 가진다. |
| K-3 | 각 verdict는 FIXED 매핑으로 정확히 하나의 fragmentationAction/Stage2Status 쌍에 정착한다 (Keep→KEEP/KEEP, Split→SPLIT/KEEP, Merge→COLLAPSE/KEEP, Reject→DROP/DROP, ManualReview→KEEP/MANUAL). |
| K-4 | `ProvenanceLinkToStage1`은 **Stage-1 계보 포인터**로 타입된다 (Stage-1 아티팩트의 행/섹션으로 해석; 일반 증거 아님). groundedBy 포인터는 이 필드로 사상한다. |
| K-5 | Merge = MergeSet(동일 부모 과분할 형제)만; RegistryCollapse는 Merge 대상이 아니다. Stage2Status COLLAPSE는 이 5개 verdict가 방출하지 않는다. |
| K-6 | conformance는 9개 필수 필드 전건 순회로 판정하며 auxiliary FragmentationDecisionReason에는 하드게이트하지 않는다. |
| K-7 | 점수 계층(FC/IC/theta) 미구축 — 점수 의존 Split/Reject 강제 금지; 구조적으로 결정 불가한 것은 ManualReview (Fork-B 4 가드). |
| K-8 | 산출 세트 C1(KEEP+SPLIT+MERGE 생존자) / ManualReviewSet(MANUAL) / ExistingIdentityReferenceSet(preserve-only)을 Stage-3 가독 섹션으로 명시 방출한다. |
| K-9 | 금지 토큰 (절대 기재 금지): collapseKind, FRAGMENT_MERGE, REGISTRY_ABSORB. |

## ClaimGrounding

E5 (claim_grounding): 각 행에 `ProvenanceLinkToStage1` 부착 — Stage-1 아티팩트의 해당 행/섹션 포인터. Stage-1의 groundedBy 포인터는 이 계보 필드 안으로 사상되었다 (원문 스팬은 읽기전용 존속).

| Stage2CandidateID | ProvenanceLinkToStage1 |
|---|---|
| S2C-01 | `_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md` § C0 Roster C0-01 / § IdentityCandidate CAND-01 (원문 L5–18, L28–43) |
| S2C-02 | 동 아티팩트 § C0 Roster C0-02 / § IdentityCandidate CAND-02 (L5–18, L44–54, L55–68) |
| S2C-03 | 동 아티팩트 § C0 Roster C0-03 / § IdentityCandidate CAND-03 (L69–85, L95–99) |
| S2C-04 | 동 아티팩트 § C0 Roster C0-04 / § IdentityCandidate CAND-04 (L86–94) |
| S2C-05 | 동 아티팩트 § C0 Roster C0-05 / § IdentityCandidate CAND-05 (L19–27, L28–43, L44–54, L86–94, L95–99) |
| S2C-05a | S2C-05 경유 — 동 아티팩트 § IdentityCandidate CAND-05 (엔드포인트 요약표 L19–27 중 `GET /` 행) |
| S2C-05b | S2C-05 경유 — 동 CAND-05 (L19–27 중 `GET /products` 행 + 상세 L28–43) |
| S2C-05c | S2C-05 경유 — 동 CAND-05 (L19–27 중 `POST /purchase` 행 + 상세 L44–54, L86–94) |
| S2C-05d | S2C-05 경유 — 동 CAND-05 (L19–27 중 `GET /purchases` 행 + 상세 L95–99) |
| S2C-06 | 동 아티팩트 § C0 Roster C0-06 / § IdentityCandidate CAND-06 (L44–54, L86–94, L100–106) |
| S2C-07 | 동 아티팩트 § C0 Roster C0-07 / § IdentityCandidate CAND-07 (L1–4, L5–18, L100–106) |
| S2C-08 | 동 아티팩트 § C0 Roster C0-08 / § IdentityCandidate CAND-08 / § ManualItem CAND-08 (L44–54, L55–68, L100–106) |
| S2C-09 | 동 아티팩트 § C0 Roster C0-09 / § IdentityCandidate CAND-09 / § ManualItem CAND-09 (L5–18, L100–106) |
| S2C-10 | 동 아티팩트 § C0 Roster C0-10 / § IdentityCandidate CAND-10 / § ManualItem CAND-10 (L1–4, L5–18, L19–27) |

## SingleAxisSeparation

E6 (single_axis_separation): 구조적 트리아지 — 과융합(over-fused) 후보를 **단일 축**으로 분리한다. 축 후보 검토 결과:

- **S2C-05 (구매 API 엔드포인트)** 가 유일한 과융합 후보. Stage-1이 "4개 진입점의 조직 축"이라는 하나의 라벨 아래에 **메서드·경로가 서로 다른 4개의 진입점**을 묶어 수확했다. 원문 스스로가 엔드포인트 요약표(L19–27)에서 4행으로 색인하고 상세 명세를 각각 별도 절로 부여하므로, 분리 축은 점수 없이 구조적으로 결정 가능하다.
- 분리 축 (단일): **엔드포인트 정체 = 메서드·경로 쌍**. 이 한 축만으로 4개 파편이 완전 분리되며 제2 축은 사용하지 않았다.
- 파편: S2C-05a `GET /`, S2C-05b `GET /products`, S2C-05c `POST /purchase`, S2C-05d `GET /purchases`. provenance는 각 파편에 읽기전용으로 운반 (ClaimGrounding 표 참조).
- 나머지 9개 C0 후보는 단일 정합 개념으로 과융합 징후 없음 — 분리 부적용.

## LateralPartition

E7 (lateral_partition): 단일 축 분해 위에서 오묶음(mis-bundled) 후보의 형제 파편화를 수행. S2C-05의 4개 파편은 동일 축 위의 **형제(sibling) 파티션**으로, 상호 배타·전체 포괄이다(요약표 4행 = 파편 4개, 잔여 없음). 그 외 후보에서 추가 오묶음은 발견되지 않아 추가 파티션 없음.

## ConceptRelationshipMap

E8 (concept_relationship_mapping): 파편·후보 간 관계 사상 (판결 참고용).

- parent→child: S2C-05 → {S2C-05a, S2C-05b, S2C-05c, S2C-05d} (분해 관계)
- sibling: S2C-05a ~ S2C-05d 상호 형제 — 단, 메서드·경로·요청/응답 형태가 각기 달라 SameRole/SameOutcome이 성립하지 않음 → 과분할 형제(MergeSet) 아님.
- 인접(참고): S2C-05c(POST /purchase)는 S2C-02(구매 요청)를 입력으로, S2C-03(구매 기록)을 산출로 가짐; S2C-05a(GET /)는 S2C-10(상품 구매 웹페이지)을 제공함 — 서로 다른 역할·범위의 별개 정체로, 병합 근거 아님.
- C0 전체에서 동일 부모 과분할 형제 쌍(SameRole ∧ SameScope ∧ SameOutcome ∧ SameSkillSurface ∧ AliasCompatible): **0쌍** → 이번 run의 MergeSet은 공집합.

## FragmentationAdjudication

E9 (identity_fragmentation_adjudication): C0 후보당 정확히 ONE verdict — score-free Fork-B 구조 트리아지, 4 가드 적용. fragmentationAction/Stage2Status는 여기서 스탬프하지 않는다. `FinalIdentityNAME`은 여기서 명명 (KEEP은 Stage-1 이름 승계, 파편은 생성 시 명명).

| Stage2CandidateID | FinalIdentityNAME | verdict | FragmentationDecisionReason (aux) |
|---|---|---|---|
| S2C-01 | 상품 (Product) | Keep | 단일 정합 엔티티; 분리·병합 축 부재 (가드 4 비해당 — 모호성 없음) |
| S2C-02 | 구매 요청 (PurchaseRequest) | Keep | 4-파라미터 고정 입력 단위로 단일 정체; 과융합 징후 없음 |
| S2C-03 | 구매 기록 (PurchaseRecord) | Keep | orderId~createdAt 필드의 단일 영속 단위 |
| S2C-04 | 오류 응답 (ErrorResponse) | Keep | 전 오류를 포괄하는 하나의 고정 형식 — 상태코드별 분리는 형식이 아닌 조건의 차이로 구조적 분리 축 아님 |
| S2C-05 | 구매 API 엔드포인트 (PurchaseApiEndpoint) | Split | 오묶음 — 메서드·경로가 다른 4개 진입점이 한 라벨에 융합; 원문 요약표가 4행으로 자체 색인하여 분리 축(메서드·경로)이 **점수 없이** 구조적으로 결정됨 (가드 1 비저촉: score-gated 아님) |
| S2C-05a | 웹페이지 제공 엔드포인트 (RootPageEndpoint) | — (파편; 부모 S2C-05의 Split 판결로 생성, 자체 C0 판결 없음) | Split 산물 — index.html 제공이라는 고유 역할 |
| S2C-05b | 상품 목록 조회 엔드포인트 (ProductListEndpoint) | — (파편) | Split 산물 — 상품 배열 반환의 고유 역할 |
| S2C-05c | 상품 구매 처리 엔드포인트 (PurchaseEndpoint) | — (파편) | Split 산물 — 핵심 구매 처리의 고유 역할 |
| S2C-05d | 구매 내역 조회 엔드포인트 (PurchaseHistoryEndpoint) | — (파편) | Split 산물 — 누적 구매 기록 반환의 고유 역할 |
| S2C-06 | 금액 검증 (AmountValidation) | Keep | 독자적 서버측 검증 규칙 단일 정체 |
| S2C-07 | 오늘마켓 API 서버 (TodayMarketApiServer) | Keep | 명세 대상 시스템 자체 — 상위 컨테이너이나 정체로서 단일 |
| S2C-08 | 지갑 주소 (WalletAddress) | ManualReview | Stage-1 defer-to-human 지속 — 필드 vs 독립 정체성 경계는 점수 계층 없이는 결정 불가 (가드 1·4: 모호 → ManualReview, 침묵 KEEP 금지) |
| S2C-09 | 인증 (Authentication) | ManualReview | 현존 아닌 예고 구조 — 정체성 선언 시점 판단은 구조적으로 결정 불가 (가드 4) |
| S2C-10 | 상품 구매 웹페이지 (PurchaseWebPage) | ManualReview | API 명세 도메인 내 독립 정체성 여부 경계선 (가드 4) |

가드 적용 요약: 가드 1(score-gated Split/Reject → ManualReview) — S2C-08~10에 적용, S2C-05의 Split은 비점수·구조 결정으로 비저촉; 가드 2(HardReject) — 해당 후보 0건; 가드 3(동일 부모 과분할 형제 → Merge) — E8 판정상 0쌍, Merge 0건; 가드 4(모호 → ManualReview) — S2C-08~10. Reject 0건 (점수 없는 Reject 강제 금지 준수).

## FragmentationSettlement

E10 (identity_fragmentation_settlement): 렌더된 verdict를 FIXED 매핑으로 정착 — 재판결 없음. `fragmentedFrom`(Split 자식→부모 역포인터)과 `collapsedFrom`(Merge 원천→생존자 목록) 기록. 전 행 9 필수 필드 완비.

| Stage2CandidateID | derivedFromStage1CandidateID | FinalIdentityNAME | NormalizedName | fragmentationAction | Stage2Status | fragmentedFrom | collapsedFrom | ProvenanceLinkToStage1 |
|---|---|---|---|---|---|---|---|---|
| S2C-01 | CAND-01 | 상품 (Product) | product | KEEP | KEEP | — | — | § ClaimGrounding S2C-01 행 (해석: Stage-1 C0-01) |
| S2C-02 | CAND-02 | 구매 요청 (PurchaseRequest) | purchase_request | KEEP | KEEP | — | — | § ClaimGrounding S2C-02 행 (Stage-1 C0-02) |
| S2C-03 | CAND-03 | 구매 기록 (PurchaseRecord) | purchase_record | KEEP | KEEP | — | — | § ClaimGrounding S2C-03 행 (Stage-1 C0-03) |
| S2C-04 | CAND-04 | 오류 응답 (ErrorResponse) | error_response | KEEP | KEEP | — | — | § ClaimGrounding S2C-04 행 (Stage-1 C0-04) |
| S2C-05 | CAND-05 | 구매 API 엔드포인트 (PurchaseApiEndpoint) | purchase_api_endpoint | SPLIT | KEEP | — (부모; forward SplitSet = {S2C-05a, S2C-05b, S2C-05c, S2C-05d}) | — | § ClaimGrounding S2C-05 행 (Stage-1 C0-05) |
| S2C-05a | CAND-05 | 웹페이지 제공 엔드포인트 (RootPageEndpoint) | root_page_endpoint | KEEP | KEEP | S2C-05 | — | § ClaimGrounding S2C-05a 행 (Stage-1 CAND-05 경유) |
| S2C-05b | CAND-05 | 상품 목록 조회 엔드포인트 (ProductListEndpoint) | product_list_endpoint | KEEP | KEEP | S2C-05 | — | § ClaimGrounding S2C-05b 행 (Stage-1 CAND-05 경유) |
| S2C-05c | CAND-05 | 상품 구매 처리 엔드포인트 (PurchaseEndpoint) | purchase_endpoint | KEEP | KEEP | S2C-05 | — | § ClaimGrounding S2C-05c 행 (Stage-1 CAND-05 경유) |
| S2C-05d | CAND-05 | 구매 내역 조회 엔드포인트 (PurchaseHistoryEndpoint) | purchase_history_endpoint | KEEP | KEEP | S2C-05 | — | § ClaimGrounding S2C-05d 행 (Stage-1 CAND-05 경유) |
| S2C-06 | CAND-06 | 금액 검증 (AmountValidation) | amount_validation | KEEP | KEEP | — | — | § ClaimGrounding S2C-06 행 (Stage-1 C0-06) |
| S2C-07 | CAND-07 | 오늘마켓 API 서버 (TodayMarketApiServer) | todaymarket_api_server | KEEP | KEEP | — | — | § ClaimGrounding S2C-07 행 (Stage-1 C0-07) |
| S2C-08 | CAND-08 | 지갑 주소 (WalletAddress) | wallet_address | KEEP | MANUAL | — | — | § ClaimGrounding S2C-08 행 (Stage-1 C0-08) |
| S2C-09 | CAND-09 | 인증 (Authentication) | authentication | KEEP | MANUAL | — | — | § ClaimGrounding S2C-09 행 (Stage-1 C0-09) |
| S2C-10 | CAND-10 | 상품 구매 웹페이지 (PurchaseWebPage) | purchase_web_page | KEEP | MANUAL | — | — | § ClaimGrounding S2C-10 행 (Stage-1 C0-10) |

정착 검산: C0 10건 — Keep 6 → KEEP/KEEP; Split 1 → SPLIT/KEEP; Merge 0; Reject 0; ManualReview 3 → KEEP/MANUAL. 파편 4행(S2C-05a~d)은 C0 판결 없이 부모 Split의 산물로 KEEP/KEEP 상태를 승계. Merge = MergeSet only 준수 — `collapsedFrom` 전 행 공집합(—). Stage2Status COLLAPSE 방출 0건.

## C1

E11 (roster_authoring): **C1 = KEEP + SPLIT + MERGE 생존자.** SPLIT 부모 S2C-05는 그 정체가 4개 파편으로 계승되어 C1에서 파편 4행이 부모를 대표한다(부모 행 자체는 SPLIT/KEEP 레코드로 존속하되, Stage-3에 넘어가는 정련 후보는 파편이다).

| C1# | Stage2CandidateID | FinalIdentityNAME | 유래 |
|---|---|---|---|
| C1-01 | S2C-01 | 상품 (Product) | KEEP (CAND-01) |
| C1-02 | S2C-02 | 구매 요청 (PurchaseRequest) | KEEP (CAND-02) |
| C1-03 | S2C-03 | 구매 기록 (PurchaseRecord) | KEEP (CAND-03) |
| C1-04 | S2C-04 | 오류 응답 (ErrorResponse) | KEEP (CAND-04) |
| C1-05 | S2C-05a | 웹페이지 제공 엔드포인트 (RootPageEndpoint) | SPLIT 파편 (CAND-05 ← S2C-05) |
| C1-06 | S2C-05b | 상품 목록 조회 엔드포인트 (ProductListEndpoint) | SPLIT 파편 (CAND-05 ← S2C-05) |
| C1-07 | S2C-05c | 상품 구매 처리 엔드포인트 (PurchaseEndpoint) | SPLIT 파편 (CAND-05 ← S2C-05) |
| C1-08 | S2C-05d | 구매 내역 조회 엔드포인트 (PurchaseHistoryEndpoint) | SPLIT 파편 (CAND-05 ← S2C-05) |
| C1-09 | S2C-06 | 금액 검증 (AmountValidation) | KEEP (CAND-06) |
| C1-10 | S2C-07 | 오늘마켓 API 서버 (TodayMarketApiServer) | KEEP (CAND-07) |

**|C1| = 10** (KEEP 6 + SPLIT 파편 4 + MERGE 0).

## ManualReviewSet

E11: Stage2Status = MANUAL 전 행.

| # | Stage2CandidateID | FinalIdentityNAME | 검토 사유 (Stage-1 ManualItem 승계 + Fork-B 근거) |
|---|---|---|---|
| MR-01 | S2C-08 | 지갑 주소 (WalletAddress) | 필드 vs 독립 정체성 경계 — 점수 계층 없이는 결정 불가 |
| MR-02 | S2C-09 | 인증 (Authentication) | 예고된 구조 — 정체성 선언 시점 판단 필요 |
| MR-03 | S2C-10 | 상품 구매 웹페이지 (PurchaseWebPage) | API 명세 도메인 내 독립 정체성 여부 경계선 |

**|ManualReviewSet| = 3.**

## ExistingIdentityReferenceSet

E11 목록화 + E12 아티팩트 SECTION 투영 (projection — member edge 아님). preserve-only 채널, **판결 없음**.

이번 run의 RegistryCollapse는 **공집합(0건)** — Stage-1의 FROZEN `_identity` 레지스트리 스냅샷에 등록 정체성이 0건이어서 보존할 기존 정체성 참조 자체가 존재하지 않는다. 공집합 상태를 명시 기록한다.

| # | 기존 정체성 참조 | collapse-target | 비고 |
|---|---|---|---|
| — | (해당 없음 — 0건) | — | 판결 미부여 채널; Merge 대상 아님 |

**|ExistingIdentityReferenceSet| = 0.**

## ArtifactLanding

E12 (artifact_landing): 본 아티팩트를 run-scope 경로에 영속 착지.

- landed path: `_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md` (runRoot = `C:\Users\jung\Desktop\Common-Context-Structure-main`)
- run-scope 방식: 공유 `_artifact/` 루트 누적 규약 — 타임스탬프 접두 `20260803_230223_` + 고정 canonical basename `stage2_identity_fragmentation_artifact.md` (Stage-1의 접두 규약과 동형; 반복 run 간 상호 덮어쓰기 없음)
- 존재 확인: 착지 후 재독으로 실재 확인 (LinkClosureCheck에서 검증 기록)
- ExistingIdentityReferenceSet은 위 섹션으로 투영 완료. 제2 아티팩트 없음 — 이 파일이 유일한 Stage-2 산출물이며, 이 착지 + 봉인이 조립의 OUTCOME이다.

## LinkClosureCheck

E13 (link_closure_check): 착지 아티팩트와 그 참조 전건에 대해 dangling 0 확인.

| 참조 | 해석 결과 |
|---|---|
| Stage-1 아티팩트 경로 `_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md` | 실재 파일로 해석 — OK |
| derivedFromStage1CandidateID CAND-01~CAND-10 (14행 전건) | Stage-1 § IdentityCandidate / § C0 Roster의 실재 행으로 전건 해석 — OK |
| ProvenanceLinkToStage1 (14행 전건) | § ClaimGrounding 표를 경유해 Stage-1 행/섹션·원문 스팬으로 전건 해석 — OK |
| fragmentedFrom = S2C-05 (4행) | 본 아티팩트 § FragmentationSettlement의 실재 부모 행 — OK |
| forward SplitSet {S2C-05a~d} | 본 아티팩트 실재 파편 행 4건 — OK |
| collapsedFrom | 전 행 공집합 — 해석 대상 없음 (명시 공집합) — OK |
| C1 / ManualReviewSet / ExistingIdentityReferenceSet 멤버 포인터 | 전건 § FragmentationSettlement의 실재 행으로 해석 — OK |

**dangling = 0.**

## InterlockCheck

E14 (interlock_check): 필드 간 인터록 검증.

| interlock | 판정 | 근거 |
|---|---|---|
| verdict ↔ fragmentationAction ↔ Stage2Status 쌍 정합 (FIXED 매핑) | conforms | Keep 6건→KEEP/KEEP, Split 1건→SPLIT/KEEP, ManualReview 3건→KEEP/MANUAL — 매핑 외 조합 0건; Merge→COLLAPSE 오기 0건; ManualReview에 action 누락 0건 (전건 KEEP) |
| Split 정합: SPLIT 행의 forward SplitSet ↔ 자식 fragmentedFrom 역포인터 | conforms | S2C-05의 SplitSet 4건 = fragmentedFrom=S2C-05인 행 4건, 상호 완전 일치 |
| Merge 정합: collapsedFrom ↔ MergeSet | conforms | 양쪽 모두 공집합 — Merge 0건 |
| C0 외 판결 부재 | conforms | verdict 보유 행 = C0 10행뿐; 파편 4행·ExistingIdentityReferenceSet(0건)에 verdict 없음 |
| 계보 정합: derivedFromStage1CandidateID ↔ ProvenanceLinkToStage1 동일 Stage-1 행 지시 | conforms | 14행 전건 동일 CAND-id 행으로 수렴 |
| 금지 토큰 부재 | conforms | collapseKind / FRAGMENT_MERGE / REGISTRY_ABSORB — 계약 인용 외 데이터 기재 0건 |

## ConformanceCheck

E15 전반부 (conformance_check): Contract(K-1~K-9)를 표준으로 착지 아티팩트에 대해 의무 전건 순회. 9개 필수 필드로 판정하며 auxiliary FragmentationDecisionReason에는 하드게이트하지 않는다.

| # | 의무 | 판정 | 근거 |
|---|---|---|---|
| 1 | K-1: C0만 verdict 수령 | conforms | verdict 10건 = C0 10행; RegistryCollapse 판결 흐름 미진입 (0건 채널 분리 유지) |
| 2 | K-1/K-5: RegistryCollapse 별도 보존 | conforms | ExistingIdentityReferenceSet 섹션에 preserve-only 공집합 명시; Merge 대상화 0건 |
| 3 | K-2: 후보당 정확히 1 verdict | conforms | C0 10행 전건 단일 verdict; 이중·누락 0건 |
| 4 | K-3: FIXED 매핑 정착 | conforms | InterlockCheck 제1 인터록 — 매핑 외 조합 0건 |
| 5 | K-5: Merge = MergeSet only | conforms | Merge 0건; collapsedFrom 전건 공집합; Stage2Status COLLAPSE 방출 0건 |
| 6 | K-4: Stage-1 계보 무결 | conforms | 14행 전건 derivedFromStage1CandidateID + ProvenanceLinkToStage1 해석 성공 (LinkClosureCheck dangling 0) |
| 7 | K-8: C1/ManualReviewSet/ExistingIdentityReferenceSet 명시 방출 | conforms | 3개 섹션 실재, 카디널리티 10/3/0 명기 |
| 8 | 9 필수 필드 전건 존재 | conforms | § FragmentationSettlement 14행 × 9필드 전건 기재 (공집합 값은 명시 —); FragmentationDecisionReason은 aux로 존재하되 게이트 미적용 |
| 9 | K-7: 점수 없는 Split/Reject 강제 금지 | conforms | Reject 0건; 유일 Split은 원문 자체 색인에 근거한 구조 결정 (가드 1 비저촉); 모호 3건 전건 ManualReview |
| 10 | K-9: 금지 토큰 부재 | conforms | InterlockCheck 확인 |

**결과: PASS** — 전 의무 충족, 비순응 0건.

## VerifiedRunRecord

E15 PASS-only 게이트 통과 (ConformanceCheck = PASS) → verified_record 실행·봉인.

```text
skill-use event: stage_2_identity_fragmentation_skill 실행 1회
  (Stage-1 입력 runID stage1_20260803_todaymarket_purchase_api 의 후속 Stage-2,
   run-scope 20260803_230223, 2026-08-03 23:02:23)

record: 위 skill-use가 본 아티팩트를 산출했다는 기록 (captured, finalized once)

named outcome (Group A):
  kind -> Stage-2 settled identity fragmentation artifact
  name -> 20260803_230223_stage2_identity_fragmentation_artifact

claim: "Stage-1 봉인 아티팩트의 C0 10건을 admit하여 후보당 정확히 하나의 verdict를
  렌더·정착(Keep 6 / Split 1→파편 4 / Merge 0 / Reject 0 / ManualReview 3)하고,
  RegistryCollapse 0건을 preserve-only 채널에 별도 보존하며,
  Stage-3 가독 산출 세트 C1(10) / ManualReviewSet(3) / ExistingIdentityReferenceSet(0)을
  단일 아티팩트로 착지, conformance PASS를 받았다"

groundedBy (Group B, ground) ->
  _artifact/20260803_230223_stage2_identity_fragmentation_artifact.md
  (본 파일; FragmentationSettlement 표 + ConformanceCheck 섹션이 검사 가능한 근거)

verification (Group B, verify): 포인터를 따라 착지 아티팩트를 재독 —
  필수 섹션 전건 존재, 14행 × 9 필수 필드 전건 기재, FIXED 매핑 정합,
  계보 해석 일치(dangling 0), 산출 세트 3종 실재, PASS 기록 실재
  verdict -> VERIFIED

converged verified record: named outcome + grounded-and-verified claim이
  이 단일 레코드로 수렴. SEALED.
```

seal: **SEALED on conformance PASS** — Stage 3는 이 아티팩트만을 읽는다.
