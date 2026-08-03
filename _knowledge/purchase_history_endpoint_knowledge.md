---
concept: PURCHASE_HISTORY_ENDPOINT
stage: knowledge
derivedFrom: "[_task/purchase_history_endpoint_task.md](../_task/purchase_history_endpoint_task.md)"
---

# purchase_history_endpoint_knowledge

purchase_history_endpoint_task 수행에 필요한 지식:

- 계약: `GET /purchases` → HTTP 200, 처리된 구매 기록 전체 JSON 배열; 파라미터 없음 (원문 L95–99).
- 원소 스키마: 구매 기록 6필드 (orderId·productName·quantity·amount·walletAddress·createdAt).
- 저장 특성: 서버 메모리 저장 — 재시작 시 초기화 (호출 측이 감안해야 할 계약).
- 용도: 확인용 (엔드포인트 요약표 L19–27 명기) — 페이징·필터 없음.
- 호출 예: `curl http://52.79.242.131/purchases`.

다음 사슬 파일: [purchase_history_endpoint_method](../_method/purchase_history_endpoint_method.md)
