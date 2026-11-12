# King Cage Korea

kingcage.rubiworkshop.com 원페이지 정적 사이트. quoc.rubiworkshop.com과 같은 구조와 디자인 체계(레이아웃, 서체, 빌드 방식)이며, 컴포넌트 브랜드용 보정은 whiteind 사이트를 따랐습니다.

- `index.html` 한국어 원페이지 (King Cage · Range · Standard · Iris · Flat Top · Side Loader · Manything · Mounts · Guide · Story · Showroom)
- 디자인은 rubi.kr 체계: 영문 Pretendard · 한글 에스코어 드림, 웨이트 400, 흑백과 얇은 라인, 각진 버튼, 라이트/다크 자동. 일본어 페이지는 빌드 시 Noto Sans JP로 바뀝니다.
- 라벨과 아이브로우는 대문자 변환 없이 원문 대소문자로 씁니다. 메뉴가 9개라 1240px 이하에서 햄버거 메뉴로 바뀝니다.
- 헤더 로고는 텍스트 워드마크(King Cage)입니다. 공식 로고는 컬러 배지라 단색으로 칠하면 뭉개지기 때문입니다. 배지 로고(`images/logo.png`)는 파비콘과 구조화 데이터에만 씁니다.
- 제품 컷(`images/cages/`, `images/parts/`)은 흰 바탕 1:1에 잘리지 않게(contain), 작업대 위 디테일과 라이프스타일 사진은 3:2로 꽉 채워(cover) 놓습니다.
- 자바스크립트가 꺼져 있어도 본문이 보이도록 등장 모션은 `html.js`일 때만 적용합니다.
- `index.src.html` 편집용 한국어 원본. 케이지 고르기 표는 `{{GUIDE_TABLE}}` 자리에 빌드 시 채워집니다 (`tools/build.py`의 `GUIDE`).
- `en/index.html`, `ja/index.html` 영어 · 일본어 페이지 (빌드로 생성, 직접 수정하지 않음)
- `i18n/tr_source.py` 한국어 · 영어 · 일본어 번역 묶음, `en.json` · `ja.json`은 여기서 생성
- `404.html` 하위 주소(/iris, /side-loader, /manything, /usb, /guide, /dealers 등)를 섹션으로 연결
- `.github/image-manifest.txt` + `fetch-images.yml` 킹 케이지 공식 스토어(kingcage.com) 이미지 이전용 워크플로

## 처음 올릴 때
1. main에 푸시하면 `fetch-images.yml`이 매니페스트의 이미지 58개를 kingcage.com에서 받아 `images/`에 커밋합니다. 공식 이미지에 PNG 스크린숏이 많아, `.jpg`로 저장할 파일은 받은 뒤 JPEG(긴 변 2400px, 품질 82)로 바꿉니다.
2. Actions → Fetch images from King Cage에서 FAIL이 있으면 해당 줄의 URL을 바꿔 다시 푸시합니다.
3. 배포: Cloudflare Pages(저장소 연결, 빌드 명령 없음, 출력 폴더 `/`) 또는 GitHub Pages(Settings → Pages → main / root).
4. 도메인 DNS에 `kingcage` CNAME 레코드를 추가합니다. CNAME 파일은 이미 들어 있습니다.

## 이미지
- 모든 사진은 킹 케이지 공식 스토어의 제품 · 소개 페이지 사진이고, 출처 URL은 `.github/image-manifest.txt`에 있습니다.
- 바꾸려면 `images/`의 파일을 지우고 매니페스트의 URL을 바꿔 푸시하거나(Actions가 받아 커밋), 같은 경로에 새 사진을 넣습니다.
- 쇼룸 섹션 사진(`brand/road.jpg`, `iris/flat-life2.jpg`)은 킹 케이지 사진이라, 루비워크샵 매장이나 루비에서 빌드한 자전거 사진으로 바꾸는 것을 권합니다.

## 문구 수정과 번역
1. `index.src.html`의 한국어 문구를 고칩니다.
2. `python3 tools/build.py` → `python3 i18n/extract.py` 로 `ko.json`을 갱신합니다.
3. 바뀐 문장을 `i18n/tr_source.py`에서 같은 한국어 키로 고치거나 (한국어, 영어, 일본어)로 추가하고 `python3 i18n/tr_source.py`.
4. 다시 `python3 tools/build.py`. 번역되지 않은 문장이 있으면 목록으로 알려줍니다.

빌드에는 `beautifulsoup4`가 필요합니다.

## 링크
- 헤더 Shop, "루비워크샵에서 보기" 버튼: `https://rubiworkshop.com/kingcage`
- 거래처 문의: 루비서플라이 02-516-8465, 카카오톡 채널 `https://pf.kakao.com/_NFnBj/chat`
- 푸터 Instagram: `https://www.instagram.com/rubi.workshop`

## 한글 표기
킹 케이지(King Cage), 론 앤드루스(Ron Andrews), 듀랑고(Durango), 아이리스(Iris), 플랫 탑(Flat Top), 사이드 로더(Side Loader), 보틀 로어링 · 보틀 레이징(Bottle Lowering · Raising), 매니씽 케이지(Manything Cage), 롱거씽 케이지(Longer Thing Cage), 올리버 케이지(Oliver Cage), 탑캡 케이지 마운트(Top Cap Cage Mount), 유니버설 서포트 볼트(Universal Support Bolt), 볼레 스트랩(Voile Straps)

## 확인이 필요한 내용
연혁(1990 원오프 티타늄 작업실, 1991 첫 티타늄 케이지, 1992 듀랑고 이주, 1996 스테인리스 케이지), 제품 설명, 금속 물통 규격(바닥 지름 2.9인치, 3인치 미만), 유니버설 서포트 볼트 크기와 주의사항, 매니씽 2리터 시험은 kingcage.com의 About · FAQ · 제품 페이지와 대조했습니다.
- 무게는 공식 스토어의 상품 데이터 값이라 실측과 조금 다를 수 있습니다 (페이지에는 "약"으로 표기).
- 팻 시티 사이클 입사 연도는 자료마다 달라(1982, 1988) 연표에는 1980s로만 적었습니다.
- "일주일에 수백 개"는 Gear Patrol 취재 기사, 1992년 듀랑고 이주와 예티 근무는 Colorado Biz 기사 기준입니다.
- 루비컴퍼니의 킹 케이지 공급 지위(공식 디스트리뷰터 여부)는 확인되지 않아 취급 문의 문구에 넣지 않았습니다.
