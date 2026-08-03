---
concept: ROOT_PAGE_ENDPOINT
stage: method
derivedFrom: "[_knowledge/root_page_endpoint_knowledge.md](../_knowledge/root_page_endpoint_knowledge.md)"
---

# root_page_endpoint_method

root_page_endpoint_knowledge를 적용하는 방법:

1. Express 앱에 루트 라우트를 등록하고 정적 index.html을 응답한다 (예: 정적 미들웨어 또는 sendFile).
2. 웹페이지 자산은 API와 같은 서버 프로세스에서 제공해 별도 배포 없이 동일 오리진을 보장한다.
3. 상품 표시 데이터는 페이지가 `GET /products`를 호출해 얻도록 하고, 페이지에 하드코딩하지 않는다.

다음 사슬 파일: [_skill/ROOT_PAGE_ENDPOINT/SKILL.md](../_skill/ROOT_PAGE_ENDPOINT/SKILL.md)
