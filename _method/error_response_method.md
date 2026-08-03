---
concept: ERROR_RESPONSE
stage: method
derivedFrom: "[_knowledge/error_response_knowledge.md](../_knowledge/error_response_knowledge.md)"
---

# error_response_method

error_response_knowledge를 적용하는 방법:

1. 실패 감지 지점마다 (완비 검사·형태 검사·금액 검증·상품 존재 검사) 사유 문자열을 조립한다.
2. 단일 방출 함수/경로로 `{success:false, error}`를 직렬화한다 — 오류 형태를 지점별로 재발명하지 않는다.
3. 상태코드는 조건표에서 기계적으로 선택한다 (검증 계열 400, 존재 계열 404).
4. 응답 후 처리를 중단한다 — 오류 방출 뒤 구매 기록 등 부수효과를 남기지 않는다.

다음 사슬 파일: [_skill/ERROR_RESPONSE/SKILL.md](../_skill/ERROR_RESPONSE/SKILL.md)
