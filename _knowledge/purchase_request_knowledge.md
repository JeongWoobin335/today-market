---
concept: PURCHASE_REQUEST
stage: knowledge
derivedFrom: "[_task/purchase_request_task.md](../_task/purchase_request_task.md)"
---

# purchase_request_knowledge

purchase_request_task 수행에 필요한 지식:

- 파라미터 계약: `productName` string(등록 상품과 일치해야 함), `quantity` integer(1 이상), `amount` number(단가×갯수와 일치해야 함), `walletAddress` string(블록체인 결제용 — 현재는 문자열 기록만).
- 4개 모두 필수 — 하나라도 누락이면 400 `{success:false, error: "필수 파라미터 누락: …"}`.
- quantity 위반 메시지: "상품갯수(quantity)는 1 이상의 정수여야 합니다." (400).
- 요청·응답은 전건 JSON; 요청 예시(원문 L55–68)가 정상 형태의 기준이다.

다음 사슬 파일: [purchase_request_method](../_method/purchase_request_method.md)
