# RoboRAVE Osaka 2026 — SoccerBot Remote 온라인 심사 시스템

축구 리모트 ES/MS/HS(32팀·105경기) 경기 운영 웹앱. 파일 하나(`index.html`)로 동작하며
Firebase 실시간 DB(`rr-osaka-resoccer`)에 결과가 저장됩니다.

## 배포 (GitHub Pages)

1. 이 저장소의 파일을 모두 업로드 (`index.html`, `.nojekyll`, `README.md`)
2. **Settings → Pages → Branch: `main` / `/ (root)`** 저장
3. 1~2분 후 접속:
   ```
   https://<계정명>.github.io/<저장소명>/
   ```

## 접속 정보 (기본값으로 내장됨)

| 항목 | 값 |
|---|---|
| DB URL | `https://rr-osaka-resoccer-default-rtdb.asia-southeast1.firebasedatabase.app` |
| 대회 코드 | `RR26-OSAKA-SOCCER` |

- 접속 화면에서 역할(관리자/심사위원/스코어보드)을 고르고 **이름만 입력**하면 됩니다.
- 8/11 진행분 13경기 결과는 이미 DB에 기록되어 있습니다.

## 심사위원 링크

배포 주소 뒤에 아래 쿼리를 붙여 나눠 주세요. (관리자 화면 → 설정 탭에서 복사 버튼으로도 생성됩니다)

```
?role=judge&field=A   필드 A (초등)
?role=judge&field=B   필드 B (중등)
?role=judge&field=C   필드 C (고등)
?role=judge&field=D   필드 D (초등)
?role=screen          스코어보드 (읽기 전용, 전체화면 ⛶)
?role=admin           관리자
```

## 8/12 운영 요약

- 오전 리그: 4개 필드 (A·D=초등, B=중등, C=고등), 10:00 시작 → 11:16경 종료
- **LSFC 5팀 경기는 전부 10:00~10:30 시작, 10:35경 완료** (11:30 기한 충족)
- LSFC는 리그전만 참가 — 결승 시드에서 자동 제외, 다음 순위 승계
- 결승 토너먼트: 13:00~14:30 (리그 종료 시 대진 자동 생성)
- 규정: 전반 90초·후반 90초 / 5점 도달 알림 / 승점 3-1-0 / 골득실 경기당 최대 5골 인정

## 대회 종료 후

- 순위표 탭 → 결과 CSV·순위표 CSV / 설정 탭 → 전체 백업(JSON) 다운로드
- Firebase 규칙을 `".read": false, ".write": false` 로 변경 (또는 DB 삭제)
