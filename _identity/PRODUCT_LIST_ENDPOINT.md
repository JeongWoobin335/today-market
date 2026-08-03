---
identity: PRODUCT_LIST_ENDPOINT
finalIdentityName: 상품 목록 조회 엔드포인트 (ProductListEndpoint)
normalizedName: product_list_endpoint
stage3SequenceID: S3S-05
stage3SequenceOrder: 5
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-05](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-06 · § FragmentationSettlement 행 S2C-05b](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-05 (요약표 GET /products 행 + 상세 L28–43) 경유](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: "[S2C-05 구매 API 엔드포인트 — Stage-2 § FragmentationSettlement 행 S2C-05 (SPLIT 부모)](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
collapsedFrom: none
sequencePreviousIdentity: "[_identity/ROOT_PAGE_ENDPOINT.md](ROOT_PAGE_ENDPOINT.md) (Stage-3 행 S3S-04)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-06 → _identity/AMOUNT_VALIDATION.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L19–27 (GET /products 행), L28–43"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PRODUCT_LIST_ENDPOINT — 상품 목록 조회 엔드포인트 (ProductListEndpoint)

`GET /products` — 판매 중인 전체 상품을 배열로 반환하는 진입점. 파라미터 없음,
HTTP 200에 `[{id, name, price, emoji, bg}, …]` JSON 배열을 응답한다 (`emoji`·`bg`는
웹페이지 표시용 보조 필드). Stage-2 SPLIT으로 S2C-05에서 분리된 파편으로,
상품 배열 반환이라는 고유 역할을 가진다. 상품(PRODUCT) 개념을 전제한다.

## Derivation

- 다음 사슬 파일: [product_list_endpoint_goal](../_goal/product_list_endpoint_goal.md)
