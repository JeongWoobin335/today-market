---
identity: PRODUCT
finalIdentityName: 상품 (Product)
normalizedName: product
stage3SequenceID: S3S-01
stage3SequenceOrder: 1
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-01](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-01 · § FragmentationSettlement 행 S2C-01](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-01 · § C0 Roster 행 C0-01](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: none
collapsedFrom: none
sequencePreviousIdentity: "none — 공집합 (Stage-3 § FollowableLinks 행 S3S-01, 최초 행)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-02 → _identity/PURCHASE_REQUEST.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L5–18, L28–43"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PRODUCT — 상품 (Product)

오늘마켓 도메인에서 전시·판매·구매의 대상이 되는 엔티티. `id`, `name`, `price`와
웹페이지 표시용 보조 필드 `emoji`, `bg`를 갖는다. 상품 목록 조회(`GET /products`)가
반환하는 배열의 원소이며, 구매 요청의 `productName` 일치 검증(404)과 금액 검증
(단가×갯수 재계산)이 전제하는 기준 데이터다. 명세 전반이 이 엔티티를 중심으로
구조화된다 (Stage-1 CAND-01 admit 근거 승계).

## Derivation

- 다음 사슬 파일: [product_goal](../_goal/product_goal.md)
