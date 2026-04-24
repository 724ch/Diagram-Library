# Archive Website Template

아카이브 웹사이트 프로젝트를 위한 템플릿이다.

## 구조

- `index.html` — 아이템 목록 페이지. 원하는대로 편집한다. 이미지 리스트가 될 수도 있고 기타 형식을 취할 수 있다.
- `item.html` — 개별 아이템 페이지. 포함된 JavaScript는 Markdown 파일을 불러와 HTML로 변환하는 역할을 한다. 이 페이지의 내용과 스크립트 등의 편집은 클로드 코드와 대화를 통해 작업한다.
- `style.css` — 스타일
- `content/` — 각 아이템의 마크다운과 미디어 파일을 이곳에 저장한다.
  - `content/<아이템-id>/index.md` — frontmatter(메타데이터) + 본문. 본문 안에도 Markdown 문법을 활용해 이미지 등을 넣을 수 있다.
  - `content/<아이템-id>/<이미지 등>` — 해당 아이템 페이지에 사용할 미디어 파일은 함께 보관한다.

새 아이템을 추가하려면:

1. `content/` 안에 새 폴더를 만든다. 폴더 이름이 아이템의 `id`가 된다. (영문 소문자, 하이픈 권장)
2. 그 폴더 안에 `index.md`를 만들고 프론트매터와 본문을 작성한다.
3. `index.html`의 `<ul>`에 `<li><a href="item.html?id=폴더이름">제목</a></li>` 한 줄을 추가한다.

## 로컬에서 실행하기

이 템플릿은 브라우저에서 `fetch()`로 마크다운 파일을 불러온다. 그래서 `index.html`을 더블클릭해서 바로 여는 방식(`file://`)으로는 동작하지 않는다. 간단한 로컬 서버가 필요하다.

VS Code의 **Live Server** 확장 프로그램을 사용하면 가장 쉽다.

1. VS Code에서 이 프로젝트 폴더를 연다.
2. Devcontainer를 통해서 다시 열어준다.
3. 확장(Extensions) 탭에서 **Live Server** (Ritwick Dey)를 설치한다. "Install in Devcontainer" 버튼이 보일 것이다.
4. `index.html` 파일을 연 상태에서 오른쪽 아래 상태바의 **Go Live** 버튼을 누른다.
   - 또는 `index.html`을 우클릭 → **Open with Live Server**.
5. 브라우저가 자동으로 열리고 `http://127.0.0.1:5500`에서 사이트가 뜬다.
6. 파일을 수정하고 저장하면 브라우저가 자동으로 새로고침된다.

중지하려면 상태바의 **Port: 5500** 버튼을 다시 누른다.

## 배포 전 확인사항

Vercel로 배포하면 업로드한 **모든 파일**이 인터넷에 공개된다. 배포하기 전에 다음을 확인하자.

- 비밀번호, API 키, 토큰 등이 파일에 남아있지 않은가?
- `content/` 폴더 안에 공개하고 싶지 않은 파일(개인 메모, 임시 파일 등)이 섞여있지 않은가?
- 업로드한 사진에 위치정보(EXIF) 등 민감한 정보가 포함되어 있지 않은가?
- 다른 사람의 글, 사진 등을 사용한 경우 저작권/출처에 문제는 없는가?

## Vercel로 배포하기

GitHub 레포를 Vercel에 연결하면 `git push` 할 때마다 자동으로 새 버전이 배포된다.

1. 이 프로젝트를 GitHub 레포에 push 해둔다 (공개/비공개 모두 가능).
2. https://vercel.com 에 GitHub 계정으로 로그인한다.
3. 상단 **Add New... → Project** 클릭.
4. 레포 목록에서 이 프로젝트를 선택 → **Import**.
5. Framework Preset은 **Other** 그대로 두고, Build/Output 설정은 건드리지 않는다 (빌드 과정이 없는 정적 사이트임).
6. **Deploy** 버튼을 누르면 몇 초 뒤 `https://<프로젝트-이름>.vercel.app` 주소가 발급된다.

이후 수정이 생기면 평소처럼 `git push` 만 하면 Vercel이 알아서 새 버전을 배포한다.
