---
concept: PRODUCT_LIST_ENDPOINT
stage: knowledge
derivedFrom: "[_task/product_list_endpoint_task.md](../_task/product_list_endpoint_task.md)"
---

# product_list_endpoint_knowledge

product_list_endpoint_task 수행에 필요한 지식:

- 계약: `GET /products` → HTTP 200, 전체 상품 JSON 배열; 파라미터 없음 (원문 L28–43).
- 응답 예: `[{ "id": 1, "name": "바나나", "price": 3000, "emoji": "🍌", "bg": "#fef9c3" }, …]`.
- `emoji`·`bg`는 웹페이지 표시용 보조 필드 — API 소비자는 무시해도 된다.
- 정본: `server.js`의 `products` 배열; 항목 추가 시 웹페이지·API에 즉시 반영.
- CORS 전체 허용 — 외부 페이지·에이전트에서 바로 호출 가능.

다음 사슬 파일: [product_list_endpoint_method](../_method/product_list_endpoint_method.md)
