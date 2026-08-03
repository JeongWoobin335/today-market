---
name: purchase_request_skill
description: 오늘마켓 구매 요청(PURCHASE_REQUEST)을 수신·검사·인도하는 종단 스킬 — 4개 필수 파라미터(productName·quantity·amount·walletAddress)의 완비·형태를 검사해 400 거절 또는 후속 검증·처리로 인도한다. Use when 구매 요청 입력 계약을 집행해야 할 때.
---

# Purchase Request Skill

구매 요청을 단일 고정 입력 계약으로 집행한다: 완비 검사 → 형태 검사 → 인도.

## Procedure

1. JSON 본문에서 `productName`, `quantity`, `amount`, `walletAddress`를 추출한다.
2. 누락이 있으면 400 `{success:false, error}`에 누락 파라미터 목록을 실어 거절한다.
3. `quantity`가 1 이상의 정수가 아니면 400으로 거절한다.
4. 통과한 요청을 변형 없이 금액 검증·구매 처리로 인도한다.

## Derivation

PURCHASE_REQUEST → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PURCHASE_REQUEST.md](../../_identity/PURCHASE_REQUEST.md)
- [_goal/purchase_request_goal.md](../../_goal/purchase_request_goal.md)
- [_task/purchase_request_task.md](../../_task/purchase_request_task.md)
- [_knowledge/purchase_request_knowledge.md](../../_knowledge/purchase_request_knowledge.md)
- [_method/purchase_request_method.md](../../_method/purchase_request_method.md)
