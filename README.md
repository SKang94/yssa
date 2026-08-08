# YSSA — Yonsei Survival Analysis Lab 홈페이지

연세대학교 생존분석연구실 홈페이지입니다. GitHub Pages(Jekyll)로 동작합니다.

---

## 1. GitHub에 올리기

1. GitHub에서 새 저장소를 만듭니다. 이름은 **`yssa`** 를 권장합니다.
   (다른 이름으로 만들면 `_config.yml` 의 `baseurl` 을 그 이름으로 바꾸세요.)

2. 이 폴더에서 아래를 실행합니다. `<사용자명>` 은 본인 GitHub 아이디입니다.

   ```bash
   git init
   git add .
   git commit -m "YSSA 홈페이지 첫 배포"
   git branch -M main
   git remote add origin https://github.com/<사용자명>/yssa.git
   git push -u origin main
   ```

3. 저장소 → **Settings → Pages** 로 이동해
   *Source* 를 **Deploy from a branch**, 브랜치를 **main / (root)** 로 지정하고 저장합니다.

4. 1~2분 뒤 `https://<사용자명>.github.io/yssa/` 에서 사이트가 열립니다.

---

## 2. 멤버 사진 넣기

사진은 **`assets/members/`** 폴더에 넣고, `_data/members.yml` 의 `photo:` 값과 파일명을 맞추면 됩니다.
사진이 없으면 이름 이니셜 아바타가 자동으로 표시되므로, 하나씩 채워 넣어도 괜찮습니다.

기존 Google Sites의 사진은 `사이트 편집 → 이미지 우클릭 → 이미지를 다른 이름으로 저장`으로 내려받을 수 있습니다.

권장 규격: 세로형(4:5 비율), 가로 400px 이상, `.jpg`

현재 `_data/members.yml` 에 적힌 파일명:

```
kang-sangwook.jpg     임지선 → lim-jiseon.jpg       박은영 → park-eunyoung.jpg
kim-dahin.jpg         박정호 → park-jeongho.jpg     김다현 → kim-dahyun.jpg
kwon-hyeokpil.jpg     신재영 → shin-jaeyoung.jpg    김가연 → kim-gayeon.jpg
song-myeonggeun.jpg   김주영 → kim-juyoung.jpg      윤지원 → yoon-jiwon.jpg
bae-soyoon.jpg
```

---

## 3. 내용 수정하기

**HTML을 건드릴 일은 거의 없습니다.** `_data/` 폴더 안의 파일만 고치면 됩니다.

| 무엇을 바꾸려면 | 어떤 파일을 |
|---|---|
| 논문 추가·수정 | `_data/publications.yml` |
| 심사 중 논문 | `_data/preprints.yml` |
| R 패키지 | `_data/software.yml` |
| 구성원 | `_data/members.yml` |
| 졸업생 | `_data/alumni.yml` |
| 연구 과제 | `_data/projects.yml` |
| 소식 | `_data/news.yml` |
| 연구실 소개 문구 · 메뉴 | `_config.yml` |

### 논문 추가 예시

`_data/publications.yml` 맨 위에 아래처럼 붙여넣으면 끝입니다.
연도별 묶음은 `year` 값을 보고 **자동으로** 만들어집니다.

```yaml
- authors: "Kim, G., J. Park, and **S. Kang**\\*"
  year: 2027
  title: "New Paper Title Goes Here"
  venue: "Biometrics"
  detail: "83(1), 1–20"
  doi: "https://doi.org/10.xxxx/xxxxx"
```

- `**...**` 로 감싼 부분은 **굵게** 표시됩니다 (강상욱 교수님 이름 강조용).
- 교신저자 별표는 `\\*` 로 씁니다.
- `detail`, `doi`, `link`, `note` 는 없으면 빼도 됩니다.

수정 후 `git add . && git commit -m "논문 추가" && git push` 하면 1~2분 뒤 사이트에 반영됩니다.
GitHub 웹사이트에서 파일을 직접 편집해도 똑같이 반영됩니다.

---

## 4. 내 컴퓨터에서 미리 보기 (선택)

```bash
gem install bundler jekyll
bundle install
bundle exec jekyll serve
```

`http://localhost:4000/yssa/` 에서 확인할 수 있습니다.

---

## 5. yssa.yonsei.ac.kr 주소를 그대로 쓰려면

1. 이 폴더에 `CNAME` 이라는 파일을 만들고 안에 `yssa.yonsei.ac.kr` 한 줄만 적습니다.
2. `_config.yml` 에서 `baseurl: ""` 로 비우고 `url: "https://yssa.yonsei.ac.kr"` 로 바꿉니다.
3. 학교 전산팀에 **`yssa` 의 CNAME 레코드를 `<사용자명>.github.io` 로 변경**해달라고 요청합니다.
4. 저장소 Settings → Pages → Custom domain 에 `yssa.yonsei.ac.kr` 을 입력합니다.
