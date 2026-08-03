---
concept: PURCHASE_ENDPOINT
stage: task
derivedFrom: "[_goal/purchase_endpoint_goal.md](../_goal/purchase_endpoint_goal.md)"
---

# purchase_endpoint_task

purchase_endpoint_goal 달성을 위해 수행할 작업:

1. `POST /purchase` 라우트를 등록하고 JSON 본문을 수신한다.
2. 구매 요청 검증을 순서대로 통과시킨다 — 파라미터 완비(400) → quantity 형태(400) → 상품 존재(404) → 금액 일치(400).
3. 전 검증 통과 시 구매 기록(orderId·productName·quantity·amount·walletAddress·createdAt)을 생성·저장한다.
4. HTTP 200으로 `{success:true, message:"구매가 완료되었습니다.", purchase:{…}}`를 반환한다.
5. 어떤 검증 실패에서도 기록을 남기지 않고 오류 응답 고정 형식으로 거절한다.

다음 사슬 파일: [purchase_endpoint_knowledge](../_knowledge/purchase_endpoint_knowledge.md)
