---
name: error_response_skill
description: 오늘마켓 오류 응답(ERROR_RESPONSE)을 단일 고정 형식으로 방출하는 종단 스킬 — 모든 실패를 {success:false, error}와 조건표 상태코드(400/404)로 수렴시킨다. Use when API 실패 경로의 응답 계약을 집행해야 할 때.
---

# Error Response Skill

모든 실패를 하나의 오류 계약으로 수렴시킨다: 사유 조립 → 고정 형식 방출 → 처리 중단.

## Procedure

1. 실패 지점에서 사유 문자열을 조립한다 (누락 목록, 기대값 대비 실제값 등).
2. `{success:false, error: 사유}` JSON만을 응답 본문으로 방출한다.
3. 상태코드를 조건표로 선택한다 — 누락/quantity/금액 불일치 400, 미등록 상품 404.
4. 방출 후 후속 처리를 중단해 부수효과를 남기지 않는다.

## Derivation

ERROR_RESPONSE → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/ERROR_RESPONSE.md](../../_identity/ERROR_RESPONSE.md)
- [_goal/error_response_goal.md](../../_goal/error_response_goal.md)
- [_task/error_response_task.md](../../_task/error_response_task.md)
- [_knowledge/error_response_knowledge.md](../../_knowledge/error_response_knowledge.md)
- [_method/error_response_method.md](../../_method/error_response_method.md)
