---
name: purchase_record_skill
description: 오늘마켓 구매 기록(PURCHASE_RECORD)을 생성·저장·공유하는 종단 스킬 — 성공한 구매만 6필드 기록으로 메모리 배열에 append하고, 성공 응답과 내역 조회가 같은 기록을 반영하게 한다. Use when 구매 이력 데이터 단위를 다뤄야 할 때.
---

# Purchase Record Skill

성공한 구매를 정확히 한 건의 완전한 기록으로 남긴다.

## Procedure

1. 검증 통과 직후 `{orderId, productName, quantity, amount, walletAddress, createdAt}`을 조립한다 (orderId 단조 증가, createdAt ISO 8601).
2. 메모리 배열에 1건 append한다 — 실패 경로에서는 절대 쓰지 않는다.
3. 같은 객체를 성공 응답 `purchase`로 반환한다.
4. 내역 조회(`GET /purchases`)가 같은 배열을 반환하게 한다 — 재시작 시 초기화됨을 계약으로 유지한다.

## Derivation

PURCHASE_RECORD → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/PURCHASE_RECORD.md](../../_identity/PURCHASE_RECORD.md)
- [_goal/purchase_record_goal.md](../../_goal/purchase_record_goal.md)
- [_task/purchase_record_task.md](../../_task/purchase_record_task.md)
- [_knowledge/purchase_record_knowledge.md](../../_knowledge/purchase_record_knowledge.md)
- [_method/purchase_record_method.md](../../_method/purchase_record_method.md)
