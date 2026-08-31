# 조회 레시피 (스킬이 언제 무엇을 부르는지)

| 시점 | 명령 | 용도 |
|---|---|---|
| 시작 직후 항상 | `bash lib/fetch.sh ctx` | 정체성·기둥·평균 조회·카드 번호 범위 |
| 시작 직후 항상 | `bash lib/fetch.sh pillars` | 기둥 미달 확인 → 기획 포인트에 반영 |
| R 번호 입력 시 | `bash lib/fetch.sh card R-###` | 레퍼런스 카드 전문 |
| 자유 주제 입력 시 | `bash lib/fetch.sh refs "키워드"` | 조회 상위 15건을 키워드 밀도로 재정렬해 최대 7건 자동 로드 (키워드 2~3개로 나눠 여러 번 가능) |
| 대표대본 갱신 요청 시 | `bash lib/fetch.sh my_top 500000` | 50만+ 릴스 대본 → 계정 폴더/대표대본/ 갱신 |

실행 위치: 항상 작업 폴더(`.env` 가 있는 곳)에서 `bash .claude/skills/릴스대본기획/lib/fetch.sh ...`.
의존: bash, curl, python3.
