---
name: product_list_endpoint_skill
description: 오늘마켓 상품 목록 조회 엔드포인트(PRODUCT_LIST_ENDPOINT, GET /products)를 운영하는 종단 스킬 — 상품 정본 전체를 HTTP 200 JSON 배열로 무파라미터 반환한다. Use when 상품 목록 공개 API를 구성·호출해야 할 때.
---

# Product List Endpoint Skill

`GET /products`로 상품 정본 전체를 일관된 배열 계약으로 공개한다.

## Procedure

1. `GET /products` 라우트를 등록한다 (요청 파라미터 없음).
2. 상품 정본 배열을 직접 참조해 변형 없이 JSON 직렬화한다.
3. HTTP 200으로 응답한다 — 원소는 `{id, name, price, emoji, bg}` 스키마.
4. 정본 변경이 즉시 반영되도록 사본·캐시를 두지 않는다.

## Derivation

PRODUCT_LIST_ENDPOINT → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PRODUCT_LIST_ENDPOINT.md](../../_identity/PRODUCT_LIST_ENDPOINT.md)
- [_goal/product_list_endpoint_goal.md](../../_goal/product_list_endpoint_goal.md)
- [_task/product_list_endpoint_task.md](../../_task/product_list_endpoint_task.md)
- [_knowledge/product_list_endpoint_knowledge.md](../../_knowledge/product_list_endpoint_knowledge.md)
- [_method/product_list_endpoint_method.md](../../_method/product_list_endpoint_method.md)
