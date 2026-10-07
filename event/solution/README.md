# HOW 개별 이벤트 페이지

- `index.html`: 독립 실행 및 로컬 확인용 전체 HTML 문서.
- `wordpress.html`: WordPress 사용자 정의 HTML 블록에 넣을 `<article>` 조각.
- `css/style.css`: 여러 페이지에서 공유 가능한 `.event_solution` 전용 CSS.
- `js/script.js`: 원본에 JavaScript가 없으므로 확장 지침만 포함한 파일.

## WordPress 적용

`wordpress.html` 내용을 사용자 정의 HTML 블록에 붙이고, 테마 또는 자식 테마에서
CSS를 `wp_enqueue_style`로 한 번 로드하세요. JS 기능을 추가하는 경우
`wp_enqueue_script`로 로드하세요. 파일 URL은 실제 업로드 경로에 맞춰 지정해야 합니다.
전체 문서인 `index.html`의 html/head/body/main을 블록에 붙이지 마세요.

WordPress SEO 플러그인/페이지 설정에서 index.html의 제목과 설명을 적용하세요.
테마가 페이지 제목을 h1으로 출력한다면 이 콘텐츠의 h1과 중복되지 않도록
해당 페이지의 테마 제목 출력을 숨기는 템플릿 설정을 사용하세요.
콘텐츠는 JavaScript 없이 검색 엔진에 노출되고 h1/h2/h3 및 Article 의미 구조를 사용합니다.
실제 URL과 게시일이 정해지면 SEO 플러그인에서 canonical과 게시일을 설정하세요.

## 재사용과 수정

모든 페이지 콘텐츠를 `.event_solution`으로 감싸고 내부 클래스는 `es-` 접두사를 사용하세요.
새 CSS 선택자와 미디어 쿼리 안의 선택자에도 `.event_solution`을 붙이세요.
색상, 최대 폭, 글꼴은 루트의 `--event-solution-*` CSS 변수를 덮어써서 바꿀 수 있습니다.
Pretendard가 사이트에 없으면 시스템 글꼴을 사용하며 외부 글꼴 요청은 없습니다.
같은 문서에 여러 인스턴스를 넣을 때에는 제목 id와 aria-labelledby를 고유하게 바꾸세요.

범위 지정은 이 CSS가 외부 요소를 바꾸는 것을 방지합니다. 테마의 강한 선택자나
!important가 컴포넌트 안에 적용되는 경우에는 실제 테마에서 추가 확인이 필요합니다.

## 로컬 확인

저장소 루트에서 `python3 -m http.server 8000 --bind 127.0.0.1`을 실행하고
로컬 요청으로 `/event/solution/index.html` 및 CSS/JS 응답을 확인하세요.
