---
concept: AMOUNT_VALIDATION
stage: method
derivedFrom: "[_knowledge/amount_validation_knowledge.md](../_knowledge/amount_validation_knowledge.md)"
---

# amount_validation_method

amount_validation_knowledge를 적용하는 방법:

1. 입력으로 (상품 객체, quantity, amount)를 받는다 — 상품은 정본 조회 결과, quantity는 형태 검증 통과값.
2. `expected = product.price * quantity`를 서버에서 계산한다.
3. `amount !== expected`이면 400 오류 형식에 상품명·갯수·기대 금액을 담아 즉시 거절한다.
4. 일치하면 검증 통과를 반환해 구매 처리(구매 기록 생성)로 진행시킨다.

다음 사슬 파일: [_skill/AMOUNT_VALIDATION/SKILL.md](../_skill/AMOUNT_VALIDATION/SKILL.md)
