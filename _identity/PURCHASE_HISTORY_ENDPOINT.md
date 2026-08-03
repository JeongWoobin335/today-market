---
identity: PURCHASE_HISTORY_ENDPOINT
finalIdentityName: 구매 내역 조회 엔드포인트 (PurchaseHistoryEndpoint)
normalizedName: purchase_history_endpoint
stage3SequenceID: S3S-09
stage3SequenceOrder: 9
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-09](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-08 · § FragmentationSettlement 행 S2C-05d](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-05 (요약표 GET /purchases 행 + 상세 L95–99) 경유](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: "[S2C-05 구매 API 엔드포인트 — Stage-2 § FragmentationSettlement 행 S2C-05 (SPLIT 부모)](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
collapsedFrom: none
sequencePreviousIdentity: "[_identity/PURCHASE_RECORD.md](PURCHASE_RECORD.md) (Stage-3 행 S3S-08)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-10 (todaymarket_api_server — Stage-4 비승격: 게이트 LEFT-SEMIJOIN 탈락, 본 run에서 정체성 파일 미발행)](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L19–27 (GET /purchases 행), L95–99"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# PURCHASE_HISTORY_ENDPOINT — 구매 내역 조회 엔드포인트 (PurchaseHistoryEndpoint)

`GET /purchases` — 지금까지 처리된 구매 기록 전체를 배열로 반환하는 확인용
진입점. 파라미터 없음. 구매 기록(PURCHASE_RECORD)이 누적되는 서버 메모리 배열을
그대로 반환하며, 서버 재시작 시 초기화된다. Stage-2 SPLIT으로 S2C-05에서 분리된
파편 중 누적 기록 반환이라는 고유 역할의 정체다.

## Derivation

- 다음 사슬 파일: [purchase_history_endpoint_goal](../_goal/purchase_history_endpoint_goal.md)
