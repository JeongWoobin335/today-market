---
concept: PURCHASE_RECORD
stage: task
derivedFrom: "[_goal/purchase_record_goal.md](../_goal/purchase_record_goal.md)"
---

# purchase_record_task

purchase_record_goal 달성을 위해 수행할 작업:

1. 구매 성공 시 6개 필드(orderId·productName·quantity·amount·walletAddress·createdAt)를 완비한 기록 객체를 생성한다.
2. `orderId`는 단조 증가로 발급하고 `createdAt`은 처리 시각(ISO 8601)으로 스탬프한다.
3. 기록을 서버 메모리 저장소 배열에 append한다.
4. 동일 기록 객체를 성공 응답의 `purchase`로 반환하고, 내역 조회가 같은 배열을 읽게 한다.

다음 사슬 파일: [purchase_record_knowledge](../_knowledge/purchase_record_knowledge.md)
