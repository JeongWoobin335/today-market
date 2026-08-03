---
concept: PRODUCT_LIST_ENDPOINT
stage: method
derivedFrom: "[_knowledge/product_list_endpoint_knowledge.md](../_knowledge/product_list_endpoint_knowledge.md)"
---

# product_list_endpoint_method

product_list_endpoint_knowledge를 적용하는 방법:

1. 라우트 핸들러에서 상품 정본 배열을 직접 읽는다 (사본·캐시를 만들지 않는다).
2. 배열을 변형 없이 JSON으로 직렬화해 HTTP 200으로 응답한다.
3. 실패 개념이 없는 단순 조회이므로 오류 분기를 도입하지 않는다 (파라미터도 없음).
4. 호출 예: `curl http://52.79.242.131/products`.

다음 사슬 파일: [_skill/PRODUCT_LIST_ENDPOINT/SKILL.md](../_skill/PRODUCT_LIST_ENDPOINT/SKILL.md)
