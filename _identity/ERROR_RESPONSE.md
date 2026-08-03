---
identity: ERROR_RESPONSE
finalIdentityName: 오류 응답 (ErrorResponse)
normalizedName: error_response
stage3SequenceID: S3S-03
stage3SequenceOrder: 3
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-03](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-04 · § FragmentationSettlement 행 S2C-04](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-04 · § C0 Roster 행 C0-04](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: none
collapsedFrom: none
sequencePreviousIdentity: "[_identity/PURCHASE_REQUEST.md](PURCHASE_REQUEST.md) (Stage-3 행 S3S-02)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-04 → _identity/ROOT_PAGE_ENDPOINT.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L86–94"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# ERROR_RESPONSE — 오류 응답 (ErrorResponse)

오늘마켓 API의 모든 오류를 포괄하는 하나의 고정 응답 형식:
`{ "success": false, "error": "사유" }`. 상태코드 조건표와 함께 규정된다 —
400 필수 파라미터 누락 / 400 quantity 1 미만 또는 비정수 / 400 amount ≠ 단가×갯수 /
404 등록되지 않은 상품명. 상태코드별 분리는 형식이 아닌 조건의 차이일 뿐,
형식은 단일 정체다 (Stage-2 Keep 근거 승계).

## Derivation

- 다음 사슬 파일: [error_response_goal](../_goal/error_response_goal.md)
