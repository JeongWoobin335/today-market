---
concept: PURCHASE_HISTORY_ENDPOINT
stage: task
derivedFrom: "[_goal/purchase_history_endpoint_goal.md](../_goal/purchase_history_endpoint_goal.md)"
---

# purchase_history_endpoint_task

purchase_history_endpoint_goal 달성을 위해 수행할 작업:

1. `GET /purchases` 라우트를 서버에 등록한다 (요청 파라미터 없음).
2. 구매 기록 메모리 배열 전체를 JSON 배열로 HTTP 200 반환한다.
3. 구매 처리와 같은 저장소를 읽어 성공 응답과 내역이 항상 일치하게 한다.

다음 사슬 파일: [purchase_history_endpoint_knowledge](../_knowledge/purchase_history_endpoint_knowledge.md)
