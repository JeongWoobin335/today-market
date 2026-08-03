---
name: product_skill
description: 오늘마켓 상품(PRODUCT) 정본을 유지·공개·참조하는 종단 스킬 — 정본 배열 유지, 목록 반환, 구매 시 상품명 존재 검증(404) 및 단가 기준 제공을 하나의 절차로 수행한다. Use when 상품 데이터를 조회·검증·확장해야 할 때.
---

# Product Skill

상품 정본을 단일 출처로 유지하고, 조회·검증·기준 제공을 그 정본 위에서 수행한다.

## Procedure

1. 정본 확인 — `server.js`의 `products` 배열을 상품의 유일한 정본으로 삼는다.
2. 목록 공개 — 목록 조회 요청에 정본 전체를 배열(JSON)로 반환한다.
3. 존재 검증 — 구매 요청의 `productName`을 정본에서 탐색; 미등록이면 404 `{success:false, error}`로 거절한다.
4. 기준 제공 — 탐색된 상품의 `price`를 금액 검증에 단가 기준으로 넘긴다.
5. 확장 — 상품 추가는 정본 배열에 항목을 추가하는 것으로 완결한다.

## Derivation

PRODUCT → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PRODUCT.md](../../_identity/PRODUCT.md)
- [_goal/product_goal.md](../../_goal/product_goal.md)
- [_task/product_task.md](../../_task/product_task.md)
- [_knowledge/product_knowledge.md](../../_knowledge/product_knowledge.md)
- [_method/product_method.md](../../_method/product_method.md)
