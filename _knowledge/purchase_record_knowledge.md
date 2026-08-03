---
concept: PURCHASE_RECORD
stage: knowledge
derivedFrom: "[_task/purchase_record_task.md](../_task/purchase_record_task.md)"
---

# purchase_record_knowledge

purchase_record_task 수행에 필요한 지식:

- 스키마: `{orderId: number, productName: string, quantity: integer, amount: number, walletAddress: string, createdAt: ISO 8601 string}` (원문 성공 응답 예 L69–85).
- 생성 조건: 전 검증을 통과한 구매 처리 성공 시에만 1건 생성 — 실패 경로는 기록을 남기지 않는다.
- 저장: 서버 메모리 배열 — 재시작 시 초기화 (원문 L95–99; 영속 DB 아님이 계약).
- 소비자: 성공 응답의 `purchase` 객체와 `GET /purchases`의 반환 배열이 이 기록을 공유한다.
- walletAddress는 현재 문자열 기록만 (향후 결제 로직 연결 예정 — 연동 참고).

다음 사슬 파일: [purchase_record_method](../_method/purchase_record_method.md)
