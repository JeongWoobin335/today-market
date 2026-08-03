---
identity: ROOT_PAGE_ENDPOINT
finalIdentityName: 웹페이지 제공 엔드포인트 (RootPageEndpoint)
normalizedName: root_page_endpoint
stage3SequenceID: S3S-04
stage3SequenceOrder: 4
derivedFromStage3: "[Stage-3 § CandidateSetForStage4 행 S3S-04](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
derivedFromStage2: "[Stage-2 § C1 행 C1-05 · § FragmentationSettlement 행 S2C-05a](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
derivedFromStage1: "[Stage-1 § IdentityCandidate 행 CAND-05 (엔드포인트 요약표 중 GET / 행) 경유](../_artifact/20260803_225737_stage1_source_linked_identity_extraction_artifact.md)"
fragmentedFrom: "[S2C-05 구매 API 엔드포인트 — Stage-2 § FragmentationSettlement 행 S2C-05 (SPLIT 부모)](../_artifact/20260803_230223_stage2_identity_fragmentation_artifact.md)"
collapsedFrom: none
sequencePreviousIdentity: "[_identity/ERROR_RESPONSE.md](ERROR_RESPONSE.md) (Stage-3 행 S3S-03)"
sequenceNextIdentity: "[Stage-3 § CandidateSetForStage4 행 S3S-05 → _identity/PRODUCT_LIST_ENDPOINT.md](../_artifact/20260803_230607_stage3_knowledge_chain_ordering_artifact.md)"
sourceSpans: "_input/_document/오늘마켓_API_명세서.md L19–27 (GET / 행)"
mintedBy: stage_4_concept_to_skill_closure_skill (4-EXEC) via candidate_sweep_skill
mintedAt: 2026-08-03
---

# ROOT_PAGE_ENDPOINT — 웹페이지 제공 엔드포인트 (RootPageEndpoint)

`GET /` — 상품 전시·결제 웹페이지(index.html)를 제공하는 진입점. Stage-2에서
과융합 후보 S2C-05(구매 API 엔드포인트)가 메서드·경로 축으로 SPLIT되며 생성된
4개 파편 중 하나로, index.html 제공이라는 고유 역할을 가진다. API 응답이 아닌
정적 웹페이지를 반환하는 유일한 엔드포인트다.

## Derivation

- 다음 사슬 파일: [root_page_endpoint_goal](../_goal/root_page_endpoint_goal.md)
