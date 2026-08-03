---
concept: ERROR_RESPONSE
stage: knowledge
derivedFrom: "[_task/error_response_task.md](../_task/error_response_task.md)"
---

# error_response_knowledge

error_response_task 수행에 필요한 지식:

- 고정 형식: `{ "success": false, "error": "사유" }` — 모든 오류가 이 한 형식 (원문 L86–94).
- 조건표: 400 필수 파라미터 누락 ("필수 파라미터 누락: productName(상품명), …") / 400 quantity 1 미만·비정수 / 400 amount ≠ 단가×갯수 ("금액 불일치: 바나나 3개의 금액은 9000원입니다. …") / 404 미등록 상품 ("존재하지 않는 상품: 사과").
- 응답은 JSON; `success`가 성공/오류 판별자다.
- 오류 형식은 구매 처리 엔드포인트(POST /purchase) 절에 결속되어 규정되나, 형식 자체는 전 오류 공통 계약이다.

다음 사슬 파일: [error_response_method](../_method/error_response_method.md)
