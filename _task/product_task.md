---
concept: PRODUCT
stage: task
derivedFrom: "[_goal/product_goal.md](../_goal/product_goal.md)"
---

# product_task

product_goal 달성을 위해 수행할 작업:

1. 상품 정본 배열을 정의·유지한다 (`server.js` 상단 `products` 배열 — 항목 추가 시 웹페이지·API 즉시 반영).
2. 목록 조회 요청에 전체 상품 배열을 무파라미터로 반환한다.
3. 구매 처리 시 상품명으로 정본에서 상품을 조회하고, 미등록 상품이면 404로 거절한다.
4. 조회된 상품의 단가를 금액 검증의 기준값으로 제공한다.

다음 사슬 파일: [product_knowledge](../_knowledge/product_knowledge.md)
