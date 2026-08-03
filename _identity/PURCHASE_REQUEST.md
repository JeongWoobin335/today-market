---
identity: PURCHASE_REQUEST
finalIdentityName: 구매 요청 (PurchaseRequest)
normalizedName: purchase_request
stage3SequenceID: S3S-02
stage3SequenceOrder: 2
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-02](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-02 · § FragmentationSettlement 행 S2C-02](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-02 · § C0 Roster 행 C0-02](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: none
collapsedFrom: none
sequencePreviousIdentity: "[_identity/PRODUCT.md](PRODUCT.md) (Stage-3 행 S3S-01)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-03 → _identity/ERROR_RESPONSE.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L5–18, L44–54, L55–68"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PURCHASE_REQUEST — 구매 요청 (PurchaseRequest)

핵심 API(`POST /purchase`)의 입력 단위. `productName`(string, 등록 상품과 일치),
`quantity`(integer, 1 이상 정수), `amount`(number, 단가×갯수와 일치),
`walletAddress`(string, 구매자 지갑 주소) — 4개 파라미터가 **모두 필수**인 고정
요청 형태다. JSON 본문으로 전달되며, 금액 검증과 구매 처리가 이 단위를 입력으로
소비한다. 파라미터 표·요청 예시·오류 조건이 이 단위를 규정한다.

## Derivation

- 다음 사슬 파일: [purchase_request_goal](../_goal/purchase_request_goal.md)
