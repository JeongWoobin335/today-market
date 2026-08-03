---
identity: AMOUNT_VALIDATION
finalIdentityName: 금액 검증 (AmountValidation)
normalizedName: amount_validation
stage3SequenceID: S3S-06
stage3SequenceOrder: 6
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-06](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-09 · § FragmentationSettlement 행 S2C-06](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-06 · § C0 Roster 행 C0-06](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: none
collapsedFrom: none
sequencePreviousIdentity: "[_identity/PRODUCT_LIST_ENDPOINT.md](PRODUCT_LIST_ENDPOINT.md) (Stage-3 행 S3S-05)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-07 → _identity/PURCHASE_ENDPOINT.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L44–54, L86–94, L100–106"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# AMOUNT_VALIDATION — 금액 검증 (AmountValidation)

서버측 금액 검증 규칙: 구매 요청의 `amount`가 상품 단가 × `quantity`와 일치하는지
서버가 **재계산**해 확인한다. 불일치 시 400 오류("금액 불일치: …")로 거절한다.
호출 측은 `amount`를 정확히 계산해 보내야 한다. 파라미터 제약(L44–54), 오류
조건표(L86–94), 연동 참고(L100–106)에 반복 등장하는 독자적 검증 규칙 정체다.

## Derivation

- 다음 사슬 파일: [amount_validation_goal](../_goal/amount_validation_goal.md)
