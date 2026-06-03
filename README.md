# Pixel Shift 개인정보 처리방침

Pixel Shift가 제공하는 여러 앱의 개인정보 처리방침을 한곳에서 게시하는 정적 사이트입니다.
GitHub Pages(조직 루트 사이트)로 배포됩니다.

- 목록(메뉴): https://pixelshift-labs.github.io/
- 넘버링카메라: https://pixelshift-labs.github.io/numbering-camera/

## 폴더 구조

```
/
├── index.html              # 랜딩 페이지 = 앱 목록(메뉴). 앱 목록의 단일 출처
├── assets/
│   └── style.css           # 모든 페이지가 공유하는 스타일
├── numbering-camera/
│   └── index.html          # 넘버링카메라 정책 (URL: /numbering-camera/)
├── 404.html                # 잘못된 경로 안내
├── .nojekyll               # Jekyll 빌드 없이 정적 파일 그대로 서빙
└── README.md
```

빌드 단계가 없는 순수 정적 HTML입니다. 파일을 그대로 서빙합니다.

## 새 앱 정책 추가하는 법

예: `awesome-app` 이라는 앱을 추가한다고 가정합니다. (`slug`는 URL에 쓰이는 영문 소문자-하이픈 이름)

1. **폴더와 정책 파일 생성**: `awesome-app/index.html` 을 만듭니다.
   - 기존 `numbering-camera/index.html` 을 복사해서 내용을 수정하는 것이 가장 빠릅니다.
   - `<head>` 안에 공용 스타일을 연결합니다: `<link rel="stylesheet" href="../assets/style.css">`
   - 카드 상단에 목록 백링크를 둡니다: `<a class="back" href="../">← 앱 목록으로</a>`
2. **목록에 링크 추가**: `index.html` 의 `<ul class="app-list">` 안에 항목을 한 줄 추가합니다.
   ```html
   <li>
     <a class="app-item" href="awesome-app/">
       <span>
         <span class="name">앱 표시 이름</span>
         <span class="desc">한 줄 설명</span>
       </span>
       <span class="arrow" aria-hidden="true">→</span>
     </a>
   </li>
   ```
3. **로컬 확인**(선택): 리포 루트에서 `python3 -m http.server` 실행 후
   `http://localhost:8000/` 와 `http://localhost:8000/awesome-app/` 를 확인합니다.
4. **배포**: 커밋 후 `main` 브랜치로 push 하면 약 1분 내 자동 반영됩니다.
   ```bash
   git add -A
   git commit -m "awesome-app 개인정보 처리방침 추가"
   git push
   ```

## 정책 본문 작성 팁

- 페이지 제목(`<title>`), 문단(`<p>`), 표(`<table>`) 등은 마크업만 맞추면 공용 스타일이 자동 적용됩니다.
- 공고/시행일자는 카드 하단 `<div class="meta">` 에 적습니다.
- 앱마다 수집 항목·권한·위탁 내용이 다르므로 본문은 앱 실제 동작에 맞게 작성하세요.
