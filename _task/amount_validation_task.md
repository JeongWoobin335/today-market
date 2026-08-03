---
concept: AMOUNT_VALIDATION
stage: task
derivedFrom: "[_goal/amount_validation_goal.md](../_goal/amount_validation_goal.md)"
---

# amount_validation_task

amount_validation_goal 달성을 위해 수행할 작업:

1. 구매 요청에서 `productName`으로 조회된 상품의 단가(`price`)를 얻는다.
2. 기대 금액 = 단가 × `quantity`를 서버측에서 재계산한다.
3. 요청의 `amount`와 기대 금액을 대조한다.
4. 불일치 시 400 오류 형식으로 기대 금액을 사유에 담아 거절하고, 일치 시에만 구매 처리를 계속한다.

다음 사슬 파일: [amount_validation_knowledge](../_knowledge/amount_validation_knowledge.md)
