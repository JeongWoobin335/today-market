---
concept: PURCHASE_REQUEST
stage: task
derivedFrom: "[_goal/purchase_request_goal.md](../_goal/purchase_request_goal.md)"
---

# purchase_request_task

purchase_request_goal 달성을 위해 수행할 작업:

1. 요청 본문을 JSON(`Content-Type: application/json`)으로 수신·파싱한다.
2. 4개 필수 파라미터의 존재를 확인하고, 누락 시 400 오류 형식으로 거절한다.
3. `quantity`가 1 이상의 정수인지 확인하고, 위반 시 400으로 거절한다.
4. 형태가 완비된 요청만 금액 검증·구매 처리 단계로 넘긴다.

다음 사슬 파일: [purchase_request_knowledge](../_knowledge/purchase_request_knowledge.md)
