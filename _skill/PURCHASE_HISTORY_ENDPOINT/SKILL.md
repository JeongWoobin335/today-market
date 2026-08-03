---
name: purchase_history_endpoint_skill
description: 오늘마켓 구매 내역 조회 엔드포인트(PURCHASE_HISTORY_ENDPOINT, GET /purchases)를 운영하는 종단 스킬 — 구매 기록 메모리 배열 전체를 무파라미터 HTTP 200 JSON 배열로 반환한다 (확인용, 재시작 초기화). Use when 누적 구매 내역 확인 API를 구성·호출해야 할 때.
---

# Purchase History Endpoint Skill

`GET /purchases`로 현재 서버 수명 내 전체 구매 기록을 확인용으로 공개한다.

## Procedure

1. `GET /purchases` 라우트를 등록한다 (요청 파라미터 없음).
2. 구매 처리가 append하는 메모리 배열을 직접 읽는다 — 사본·캐시 금지.
3. 변형 없이 JSON 배열로 HTTP 200 응답한다 (기록 0건이면 `[]`).
4. 메모리 휘발성(서버 재시작 시 초기화)을 계약으로 유지한다.

## Derivation

PURCHASE_HISTORY_ENDPOINT → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PURCHASE_HISTORY_ENDPOINT.md](../../_identity/PURCHASE_HISTORY_ENDPOINT.md)
- [_goal/purchase_history_endpoint_goal.md](../../_goal/purchase_history_endpoint_goal.md)
- [_task/purchase_history_endpoint_task.md](../../_task/purchase_history_endpoint_task.md)
- [_knowledge/purchase_history_endpoint_knowledge.md](../../_knowledge/purchase_history_endpoint_knowledge.md)
- [_method/purchase_history_endpoint_method.md](../../_method/purchase_history_endpoint_method.md)
