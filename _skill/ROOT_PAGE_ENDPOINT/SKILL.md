---
name: root_page_endpoint_skill
description: 오늘마켓 웹페이지 제공 엔드포인트(ROOT_PAGE_ENDPOINT, GET /)를 운영하는 종단 스킬 — 상품 전시·결제 UI(index.html)를 API와 같은 서버에서 동일 오리진으로 제공한다. Use when 루트 진입점/웹페이지 제공을 구성해야 할 때.
---

# Root Page Endpoint Skill

`GET /` 진입점을 통해 상품 전시·결제 웹페이지를 제공한다.

## Procedure

1. Express 앱에 `GET /` 라우트를 등록한다.
2. index.html(상품 전시·결제 UI)을 응답한다 — 이 진입점만 HTML을 반환한다.
3. 페이지가 동일 오리진의 `GET /products`·`POST /purchase`를 호출하도록 유지한다.
4. 웹페이지와 API를 하나의 Node.js(Express) 서버 프로세스로 함께 서비스한다.

## Derivation

ROOT_PAGE_ENDPOINT → goal → task → knowledge → method → skill 사슬의 종단:

- [_identity/ROOT_PAGE_ENDPOINT.md](../../_identity/ROOT_PAGE_ENDPOINT.md)
- [_goal/root_page_endpoint_goal.md](../../_goal/root_page_endpoint_goal.md)
- [_task/root_page_endpoint_task.md](../../_task/root_page_endpoint_task.md)
- [_knowledge/root_page_endpoint_knowledge.md](../../_knowledge/root_page_endpoint_knowledge.md)
- [_method/root_page_endpoint_method.md](../../_method/root_page_endpoint_method.md)
