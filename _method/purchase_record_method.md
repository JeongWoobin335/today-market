---
concept: PURCHASE_RECORD
stage: method
derivedFrom: "[_knowledge/purchase_record_knowledge.md](../_knowledge/purchase_record_knowledge.md)"
---

# purchase_record_method

purchase_record_knowledge를 적용하는 방법:

1. 생성 — 검증 통과 직후 요청 필드 + 발급 orderId + 현재 시각 createdAt으로 기록 객체를 조립한다.
2. 저장 — 메모리 배열에 append한다 (유일한 쓰기 지점; 실패 경로에서 호출 금지).
3. 공유 — 같은 객체를 성공 응답에 싣고, 내역 조회는 같은 배열을 그대로 반환한다.
4. 휘발성 명시 — 재시작 초기화를 소비자에게 계약으로 알린다 (확인용 조회라는 성격 유지).

다음 사슬 파일: [_skill/PURCHASE_RECORD/SKILL.md](../_skill/PURCHASE_RECORD/SKILL.md)
