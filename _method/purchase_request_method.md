---
concept: PURCHASE_REQUEST
stage: method
derivedFrom: "[_knowledge/purchase_request_knowledge.md](../_knowledge/purchase_request_knowledge.md)"
---

# purchase_request_method

purchase_request_knowledge를 적용하는 방법:

1. 수신 — JSON 본문을 파싱해 4개 필드를 추출한다.
2. 완비 검사 — 누락 필드 목록을 만들고, 비어 있지 않으면 400 오류 형식에 누락 목록을 실어 즉시 반환한다.
3. 형태 검사 — `quantity`를 정수·1 이상 조건으로 검사하고 위반 시 400 반환한다.
4. 인도 — 통과한 요청 객체를 그대로 금액 검증(amount_validation) → 구매 처리(purchase_endpoint)로 인도한다 (필드 변형 없음).

다음 사슬 파일: [_skill/PURCHASE_REQUEST/SKILL.md](../_skill/PURCHASE_REQUEST/SKILL.md)
