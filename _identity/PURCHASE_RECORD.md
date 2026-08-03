---
identity: PURCHASE_RECORD
finalIdentityName: 구매 기록 (PurchaseRecord)
normalizedName: purchase_record
stage3SequenceID: S3S-08
stage3SequenceOrder: 8
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-08](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-03 · § FragmentationSettlement 행 S2C-03](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-03 · § C0 Roster 행 C0-03](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: none
collapsedFrom: none
sequencePreviousIdentity: "[_identity/PURCHASE_ENDPOINT.md](PURCHASE_ENDPOINT.md) (Stage-3 행 S3S-07)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-09 → _identity/PURCHASE_HISTORY_ENDPOINT.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L69–85, L95–99"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PURCHASE_RECORD — 구매 기록 (PurchaseRecord)

구매 처리가 성공할 때 생성되는 영속(메모리) 단위. `orderId`, `productName`,
`quantity`, `amount`, `walletAddress`, `createdAt` 필드를 가지며, 성공 응답의
`purchase` 객체로 반환되고 `GET /purchases`가 반환하는 누적 배열의 원소가 된다.
서버 메모리에 저장되어 서버 재시작 시 초기화된다.

## Derivation

- 다음 사슬 파일: [purchase_record_goal](../_goal/purchase_record_goal.md)
