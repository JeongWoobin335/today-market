---
identity: PURCHASE_ENDPOINT
finalIdentityName: 상품 구매 처리 엔드포인트 (PurchaseEndpoint)
normalizedName: purchase_endpoint
stage3SequenceID: S3S-07
stage3SequenceOrder: 7
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-07](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-07 · § FragmentationSettlement 행 S2C-05c](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-05 (요약표 POST /purchase 행 + 상세 L44–54, L86–94) 경유](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: "[S2C-05 구매 API 엔드포인트 — Stage-2 § FragmentationSettlement 행 S2C-05 (SPLIT 부모)](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
collapsedFrom: none
sequencePreviousIdentity: "[_identity/AMOUNT_VALIDATION.md](AMOUNT_VALIDATION.md) (Stage-3 행 S3S-06)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-08 → _identity/PURCHASE_RECORD.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L19–27 (POST /purchase 행), L44–54, L69–85, L86–94"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PURCHASE_ENDPOINT — 상품 구매 처리 엔드포인트 (PurchaseEndpoint)

`POST /purchase` — 상품 구매를 처리하는 **핵심 API**. 구매 요청(PURCHASE_REQUEST)
을 입력으로 받아 파라미터 완비·형태 검증, 상품 존재 검증(404), 금액 검증
(AMOUNT_VALIDATION)을 통과시킨 뒤 구매 기록(PURCHASE_RECORD)을 생성하고 성공
응답 `{success:true, message, purchase}`(HTTP 200)를 반환한다. 모든 실패는 오류
응답(ERROR_RESPONSE) 고정 형식으로 방출한다. Stage-2 SPLIT으로 S2C-05에서 분리된
파편 중 핵심 처리 역할의 정체다.

## Derivation

- 다음 사슬 파일: [purchase_endpoint_goal](../_goal/purchase_endpoint_goal.md)
