---
concept: PRODUCT
stage: knowledge
derivedFrom: "[_task/product_task.md](../_task/product_task.md)"
---

# product_knowledge

product_task 수행에 필요한 지식:

- 상품 스키마: `id`(number), `name`(string), `price`(number), `emoji`·`bg`(웹페이지 표시용 보조 필드 — API 계약상 필수 의미 없음).
- 등록된 상품만 구매 가능: `productName` 불일치 시 404 `{success:false, error}` 응답.
- 금액 기준: `amount`는 반드시 해당 상품 `price` × `quantity`와 일치해야 하며 서버가 재계산 검증한다.
- 정본 위치: `server.js`의 `products` 배열이 유일한 상품 정본이다 (별도 저장소 없음).

다음 사슬 파일: [product_method](../_method/product_method.md)
