---
concept: ERROR_RESPONSE
stage: task
derivedFrom: "[_goal/error_response_goal.md](../_goal/error_response_goal.md)"
---

# error_response_task

error_response_goal 달성을 위해 수행할 작업:

1. 실패 조건을 감지한 지점에서 사유 문자열을 만든다 (누락 목록·검증 실패 설명 포함).
2. `{success:false, error: 사유}` 형식으로만 응답 본문을 구성한다 (다른 오류 형태 금지).
3. 조건에 맞는 상태코드를 부여한다 — 파라미터 누락·quantity 위반·금액 불일치는 400, 미등록 상품은 404.
4. 성공 응답(`success:true`)과 형식 충돌이 없도록 `success` 필드를 판별자로 유지한다.

다음 사슬 파일: [error_response_knowledge](../_knowledge/error_response_knowledge.md)
