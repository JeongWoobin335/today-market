---
concept: PURCHASE_ENDPOINT
stage: method
derivedFrom: "[_knowledge/purchase_endpoint_knowledge.md](../_knowledge/purchase_endpoint_knowledge.md)"
---

# purchase_endpoint_method

purchase_endpoint_knowledge를 적용하는 방법:

1. 수신 — JSON 본문 파싱 후 구매 요청 검사 절차(purchase_request_method)를 먼저 통과시킨다.
2. 조회 — `productName`으로 상품 정본을 탐색한다; 실패 시 404 거절 (product_method).
3. 검증 — 금액 검증 절차(amount_validation_method)로 단가×갯수 대조; 실패 시 400 거절.
4. 처리 — 통과 시에만 구매 기록을 생성해 메모리 저장소에 append하고 (orderId 증가, createdAt ISO 스탬프), 성공 응답을 반환한다.
5. 원자성 — 거절 경로에서는 저장소를 건드리지 않는다; 성공 경로에서만 1건 append.

다음 사슬 파일: [_skill/PURCHASE_ENDPOINT/SKILL.md](../_skill/PURCHASE_ENDPOINT/SKILL.md)
