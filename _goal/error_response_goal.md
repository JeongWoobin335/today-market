---
concept: ERROR_RESPONSE
stage: goal
derivedFrom: "[_identity/ERROR_RESPONSE.md](../_identity/ERROR_RESPONSE.md)"
---

# error_response_goal

ERROR_RESPONSE 정체성에서 유도한 목표: 어떤 실패 경로에서도 클라이언트가
`{success:false, error}` 단일 형식과 적절한 상태코드(400/404)만을 받도록 하여,
호출 측이 오류 파싱을 하나의 계약으로 처리할 수 있는 상태를 이룬다.

다음 사슬 파일: [error_response_task](../_task/error_response_task.md)
