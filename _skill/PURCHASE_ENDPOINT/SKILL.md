---
name: purchase_endpoint_skill
description: 오늘마켓 상품 구매 처리 엔드포인트(PURCHASE_ENDPOINT, POST /purchase)를 운영하는 종단 스킬 — 완비·형태·존재·금액 검증을 순서대로 통과시킨 뒤에만 구매 기록을 생성하고 성공 응답을 반환한다. Use when 핵심 구매 처리 API를 구성해야 할 때.
---

# Purchase Endpoint Skill

핵심 구매 처리: 전건 검증 → 원자적 기록 → 계약된 응답.

## Procedure

1. `POST /purchase`로 JSON 구매 요청을 수신한다.
2. 검증 사슬을 순서대로 집행한다 — 파라미터 완비(400) → quantity 정수·1 이상(400) → 상품 존재(404) → 금액 = 단가×갯수(400).
3. 전 검증 통과 시 구매 기록 `{orderId, productName, quantity, amount, walletAddress, createdAt}`을 메모리 저장소에 1건 append한다.
4. HTTP 200 `{success:true, message:"구매가 완료되었습니다.", purchase}`를 반환한다.
5. 어떤 실패에서도 기록 없이 `{success:false, error}` 고정 형식으로 거절한다.

## Derivation

PURCHASE_ENDPOINT → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PURCHASE_ENDPOINT.md](../../_identity/PURCHASE_ENDPOINT.md)
- [_goal/purchase_endpoint_goal.md](../../_goal/purchase_endpoint_goal.md)
- [_task/purchase_endpoint_task.md](../../_task/purchase_endpoint_task.md)
- [_knowledge/purchase_endpoint_knowledge.md](../../_knowledge/purchase_endpoint_knowledge.md)
- [_method/purchase_endpoint_method.md](../../_method/purchase_endpoint_method.md)
