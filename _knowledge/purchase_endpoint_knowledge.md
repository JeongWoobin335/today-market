---
concept: PURCHASE_ENDPOINT
stage: knowledge
derivedFrom: "[_task/purchase_endpoint_task.md](../_task/purchase_endpoint_task.md)"
---

# purchase_endpoint_knowledge

purchase_endpoint_task 수행에 필요한 지식:

- 입력 계약: 구매 요청 4개 필수 파라미터 (productName/quantity/amount/walletAddress) — L44–54.
- 성공 계약: HTTP 200 `{success:true, message:"구매가 완료되었습니다.", purchase:{orderId, productName, quantity, amount, walletAddress, createdAt}}` — L69–85.
- 실패 계약: 전 오류 `{success:false, error}` — 400 누락 / 400 quantity / 400 금액 불일치 / 404 미등록 상품 — L86–94.
- 검증 의존: 상품 존재·단가는 상품 정본에서, 금액은 서버측 재계산에서 얻는다.
- 기록 의존: 성공 시 구매 기록이 메모리 저장소에 누적된다 (`GET /purchases`가 반환).
- walletAddress는 현재 문자열 기록만 — 이후 결제 처리 로직이 server.js에 연결될 수 있다.

다음 사슬 파일: [purchase_endpoint_method](../_method/purchase_endpoint_method.md)
