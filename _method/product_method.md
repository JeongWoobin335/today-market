---
concept: PRODUCT
stage: method
derivedFrom: "[_knowledge/product_knowledge.md](../_knowledge/product_knowledge.md)"
---

# product_method

product_knowledge를 적용하는 방법:

1. 조회 경로 — 목록 요청이 오면 정본 배열을 그대로 직렬화해 반환한다 (변형·필터 없음).
2. 검증 경로 — 구매 요청의 `productName`으로 정본을 탐색한다: 실패 → 404 오류 형식 방출; 성공 → 상품 객체를 얻는다.
3. 기준 제공 경로 — 얻은 상품의 `price`를 금액 검증 절차(단가×갯수 재계산)에 넘긴다.
4. 유지 경로 — 상품 추가·변경은 정본 배열 한 곳만 수정한다.

다음 사슬 파일: [_skill/PRODUCT/SKILL.md](../_skill/PRODUCT/SKILL.md)
