---
concept: AMOUNT_VALIDATION
stage: knowledge
derivedFrom: "[_task/amount_validation_task.md](../_task/amount_validation_task.md)"
---

# amount_validation_knowledge

amount_validation_task 수행에 필요한 지식:

- 규칙: `amount`(number)는 반드시 단가 × 갯수와 일치해야 한다 (원문 L44–54).
- 검증 주체: 서버 — 서버가 단가×갯수를 재계산해 검증하므로 호출 측은 `amount`를 정확히 계산해 보내야 한다 (L100–106).
- 실패 계약: 400 `{success:false, error}` — 예: "금액 불일치: 바나나 3개의 금액은 9000원입니다. …" (L86–94).
- 단가 출처: 상품 정본(`products` 배열)의 `price` — 클라이언트 제시 값이 아니다.
- 전제: quantity는 이미 1 이상의 정수로 검증된 상태에서 곱셈이 의미를 가진다.

다음 사슬 파일: [amount_validation_method](../_method/amount_validation_method.md)
