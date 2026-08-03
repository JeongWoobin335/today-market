# 오늘마켓 구매 API 명세서

> 상품 구매 웹페이지 · 구매 처리 REST API | v1.0 | 2026. 8. 3. | 작성: 정우빈

## 1. 개요

상품(바나나, 우유)을 전시하고 결제를 처리하는 웹페이지와, 상품 구매를 처리하는 REST API입니다.
웹페이지와 API는 하나의 Node.js(Express) 서버가 함께 제공하며, 구매 요청은 상품명·상품갯수·금액·지갑주소 4개 파라미터를 받습니다.

| 항목 | 내용 |
|---|---|
| 기술 스택 | Node.js 22 · Express 5 · CORS 허용 |
| Base URL (배포) | `http://52.79.242.131` |
| Base URL (로컬) | `http://localhost:3000` |
| 데이터 형식 | 요청·응답 모두 JSON (`Content-Type: application/json`) |
| 인증 | 없음 (데모용) · 추후 지갑 서명 검증 연동 예정 |
| 실행 방법 (로컬) | `cd api` → `npm install` → `npm start` |

## 2. 엔드포인트 요약

| 메서드 · 경로 | 설명 |
|---|---|
| `GET /` | 웹페이지(index.html) 제공 |
| `GET /products` | 판매 상품 목록 조회 |
| `POST /purchase` | 상품 구매 처리 **(핵심 API)** |
| `GET /purchases` | 누적 구매 내역 조회 (확인용) |

## 3. 상세 명세

### GET /products — 상품 목록 조회

판매 중인 전체 상품을 배열로 반환합니다. 파라미터 없음.

```json
HTTP 200
[
  { "id": 1, "name": "바나나", "price": 3000, "emoji": "🍌", "bg": "#fef9c3" },
  { "id": 2, "name": "우유",   "price": 2500, "emoji": "🥛", "bg": "#eff6ff" }
]
```

> `emoji`, `bg`는 웹페이지 표시용 보조 필드입니다.

### POST /purchase — 상품 구매 처리

요청 본문(Body) 파라미터 — **4개 모두 필수**:

| 파라미터 | 타입 | 설명 | 예시 |
|---|---|---|---|
| `productName` | string | 상품명 (등록된 상품과 일치해야 함) | `"바나나"` |
| `quantity` | integer | 상품 갯수 (1 이상의 정수) | `3` |
| `amount` | number | 금액 (단가 × 갯수와 일치해야 함) | `9000` |
| `walletAddress` | string | 구매자 지갑 주소 (블록체인 결제용) | `"7xKXtg2CW8..."` |

**요청 예시:**

```json
POST /purchase
Content-Type: application/json

{
  "productName": "바나나",
  "quantity": 3,
  "amount": 9000,
  "walletAddress": "7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU"
}
```

**성공 응답 (HTTP 200):**

```json
{
  "success": true,
  "message": "구매가 완료되었습니다.",
  "purchase": {
    "orderId": 1,
    "productName": "바나나",
    "quantity": 3,
    "amount": 9000,
    "walletAddress": "7xKXtg2CW87d97TXJSDpbD5jBkheTqA83TZRuJosgAsU",
    "createdAt": "2026-08-03T07:50:39.660Z"
  }
}
```

**오류 응답** — 모든 오류는 `{ "success": false, "error": "사유" }` 형식:

| 상태 코드 | 발생 조건 | 오류 메시지 예시 |
|---|---|---|
| 400 | 필수 파라미터 누락 | 필수 파라미터 누락: productName(상품명), ... |
| 400 | quantity가 1 미만 또는 정수가 아님 | 상품갯수(quantity)는 1 이상의 정수여야 합니다. |
| 400 | amount ≠ 단가 × 갯수 | 금액 불일치: 바나나 3개의 금액은 9000원입니다. ... |
| 404 | 등록되지 않은 상품명 | 존재하지 않는 상품: 사과 |

### GET /purchases — 구매 내역 조회

지금까지 처리된 구매 기록 전체를 배열로 반환합니다. 파라미터 없음.
구매 기록은 서버 메모리에 저장되므로 서버 재시작 시 초기화됩니다.

## 4. 연동 참고 사항

- **금액 검증**: 서버가 단가×갯수를 재계산해 검증하므로, 호출 측은 `amount`를 정확히 계산해 보내야 합니다.
- **지갑주소**: 현재는 문자열로 기록만 하며, 이후 결제 처리 로직이 `server.js`의 구매 처리 부분에 연결될 수 있도록 되어 있습니다.
- **CORS**: 모든 출처(Origin)에 대해 허용되어 있어 외부 페이지·에이전트에서 바로 호출 가능합니다.
- **상품 추가**: `server.js` 상단의 `products` 배열에 항목을 추가하면 웹페이지와 API에 즉시 반영됩니다.

## 5. 호출 빠른 시작 (curl)

```bash
# 상품 목록
curl http://52.79.242.131/products

# 구매
curl -X POST http://52.79.242.131/purchase \
  -H "Content-Type: application/json" \
  -d '{"productName":"바나나","quantity":3,"amount":9000,"walletAddress":"지갑주소"}'

# 구매 내역
curl http://52.79.242.131/purchases
```
