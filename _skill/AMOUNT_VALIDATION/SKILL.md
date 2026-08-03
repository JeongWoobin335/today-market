---
name: amount_validation_skill
description: 오늘마켓 금액 검증(AMOUNT_VALIDATION)을 집행하는 종단 스킬 — 서버가 단가×갯수를 재계산해 요청 amount와 대조하고, 불일치면 400으로 거절, 일치 시에만 구매 처리를 통과시킨다. Use when 구매 금액의 서버측 검증을 구성해야 할 때.
---

# Amount Validation Skill

클라이언트 금액을 신뢰하지 않는다: 재계산 → 대조 → 거절 또는 통과.

## Procedure

1. 정본에서 조회된 상품의 `price`와 검증된 `quantity`로 기대 금액을 재계산한다.
2. 요청 `amount`와 기대 금액을 대조한다.
3. 불일치 시 400 `{success:false, error: "금액 불일치: …"}`로 즉시 거절한다.
4. 일치 시에만 구매 처리(기록 생성)로 진행시킨다.

## Derivation

AMOUNT_VALIDATION → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/AMOUNT_VALIDATION.md](../../_identity/AMOUNT_VALIDATION.md)
- [_goal/amount_validation_goal.md](../../_goal/amount_validation_goal.md)
- [_task/amount_validation_task.md](../../_task/amount_validation_task.md)
- [_knowledge/amount_validation_knowledge.md](../../_knowledge/amount_validation_knowledge.md)
- [_method/amount_validation_method.md](../../_method/amount_validation_method.md)
