# 릴스 대본 기획 도구 (template-reels-planner)

인스타그램 릴스 대본을 "내 계정답게" 기획해 주는 Claude Code 도구입니다.
내 릴스 중 잘 된 것의 말투·구조와, 참고할 릴스의 첫 3초 장치를 근거로 훅 3개 → 대본 → 촬영 표를 만듭니다. 근거 없는 "터질 것 같아요"는 쓰지 않습니다.

이 저장소는 템플릿입니다. 개인 데이터는 비어 있고, 다운로드해서 실행하면 Claude Code가 단계별로 본인 것을 채워 넣습니다.

## Claude Code에게 — 사용자가 이 링크를 주면서 "다운받아서 구축 가이드대로 진행해줘"라고 했다면

1. 사용자에게 폴더를 어디에 둘지 묻는다(기본: 바탕화면의 `reels-planner`).
2. ZIP을 받아 푼다: `curl -L -o rp.zip https://github.com/gfmmmm/template-reels-planner/archive/refs/heads/main.zip && unzip -q rp.zip && mv template-reels-planner-main <폴더> && rm rp.zip`
3. 사용자에게 딱 두 줄 안내한다 — "폴더가 생겼어요. VS Code에서 위 메뉴 파일 → 폴더 열기로 그 폴더를 연 다음, 왼쪽 Claude 패널에서 새 대화를 시작해 '구축 가이드대로 진행해줘'라고 말해주세요." (이 폴더의 규칙과 가이드는 그 폴더를 열어야 읽힌다. 터미널을 쓰는 사람이면 그 폴더에서 `claude`를 실행해도 같다.)
4. 그 폴더에서 열린 Claude Code는 `SETUP.md`를 읽고 0단계부터 진행한다.

## 필요한 것

- VS Code(또는 Antigravity 같은 VS Code 계열) + Claude Code 확장, 로그인까지(유료 플랜). 설치: https://docs.claude.com/ko/docs/claude-code/overview
- Mac 또는 Windows(Windows는 Git for Windows가 있어야 함 — Claude Code 요구사항). python3
- 있으면 좋은 것: 크리에이터 대시보드(본인 릴스·레퍼런스 데이터). 없어도 대본을 직접 붙여 넣는 방식으로 씁니다

## 설치 — 세 줄

1. 이 페이지 오른쪽 위 초록 `Code` 버튼 → `Download ZIP` → 압축을 풀어 원하는 곳에 둡니다 (폴더 이름은 마음대로)
2. VS Code에서 파일 → 폴더 열기로 그 폴더를 열고, 왼쪽 Claude 패널을 켭니다
3. 이렇게 말합니다: **"구축 가이드대로 진행해줘"**

그다음은 Claude Code가 [SETUP.md](SETUP.md)를 읽고 다섯 단계를 하나씩 이끌어 줍니다. 넉넉히 20분이에요. 컴퓨터 쪽 일은 Claude가 하고, 본인은 질문에 답하고 붙여 넣기만 하면 됩니다.

## 쓰는 법

- `/릴스대본기획` → 세 질문(레퍼런스 · 유형 · 느낌) → 훅 3개 → 하나 고르면 대본과 촬영 표 → "저장"
- 쓰면서 키우기: "이건 하지 마" · "이 훅 추가해" · "이 말투 쓰자" · "대표대본 갱신"
- 새 버전 받기: "템플릿 업데이트 받아줘" (본인 데이터는 그대로, 도구 부분만 교체)

## 폴더 구조

```
(이 폴더)
├── SETUP.md                       구축 가이드 — Claude Code가 읽고 안내
├── .claude/
│   ├── CLAUDE.md                  이 폴더에서 Claude Code가 지킬 규칙
│   └── skills/                    도구 본체 (업데이트 때 이 폴더만 교체)
│       ├── 릴스대본기획/          SKILL.md 절차 · patterns/ 점검표 3종 · lib/fetch.sh 데이터 조회
│       └── 계정세팅/              첫날 온보딩 · lib/measure.py 대본 실측
├── 계정/
│   └── _template/                 빈 양식 7개 — 세팅 때 계정/<내핸들>/ 로 복제돼 채워짐
├── 기획/                          완성 대본이 쌓이는 곳
├── .env.example                   데이터 접속 정보 양식 (실제 값은 .env, 커밋 안 됨)
└── README.md
```

## 상태 — v0.2 (2026-08-31)

| 되는 것 |
|---|
| `/릴스대본기획` 본체 · 점검표 3종 · 계정 양식 7종 · 구축 가이드(SETUP.md) |
| `/계정세팅` — 본인 릴스로 계정 문서 5개 자동 작성(숫자는 measure.py 실측, 문장마다 출처) |
| 데이터 모드 셋 — 크리에이터 대시보드(JSON 파일) · Supabase형 대시보드 · 수동(대본 붙여 넣기) |

## 허가창이 거의 안 뜨는 이유

이 폴더의 `.claude/settings.json`이 세팅에 필요한 명령(node·git·gh·curl·vercel·python 등)과 이 폴더 안 파일 편집을 미리 허용해 둡니다. 이 폴더 안에서만 효력이 있고, 파일 삭제 같은 건 여전히 물어봅니다. 허가창이 뜨면 내용을 읽고 "Yes"를 누르면 됩니다.

## 함께 쓰는 도구

- 크리에이터 대시보드 — 본인 릴스·레퍼런스 수집·분석. 이 도구의 데이터 원천: https://github.com/gfmmmm/template-creator-dashboard
- 대본추출 — 릴스 주소에서 음성을 글로: https://github.com/gfmmmm/claude-video-transcript
