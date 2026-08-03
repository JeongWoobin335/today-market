---
concept: PRODUCT_LIST_ENDPOINT
stage: task
derivedFrom: "[_goal/product_list_endpoint_goal.md](../_goal/product_list_endpoint_goal.md)"
---

# product_list_endpoint_task

product_list_endpoint_goal 달성을 위해 수행할 작업:

1. `GET /products` 라우트를 서버에 등록한다 (요청 파라미터 없음).
2. 상품 정본 배열 전체를 HTTP 200 + JSON 배열로 반환한다.
3. 반환 원소가 상품 스키마(id/name/price/emoji/bg)를 온전히 담도록 한다.
4. 상품 정본 변경(추가)이 즉시 응답에 반영되도록 정본을 직접 참조한다.

다음 사슬 파일: [product_list_endpoint_knowledge](../_knowledge/product_list_endpoint_knowledge.md)
