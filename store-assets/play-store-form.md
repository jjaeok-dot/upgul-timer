# Google Play Console 등록 폼 — 미리 작성 텍스트

> Galaxy Store 등록이 정책상 막혔어서 **Google Play Console**의 **Closed Testing(클로즈드 테스트)** 트랙으로 가는 길입니다. 프로덕션 출시는 안 합니다 (20명/14일 룰 회피).
>
> 이 파일을 메모장으로 열고 각 칸에 그대로 복사·붙여넣기 하시면 됩니다.

---

## 0. 시작하기 — Play Console 가입

1. https://play.google.com/console/signup
2. 본인 Google 계정으로 로그인 (`jjaeok@gmail.com`)
3. **개인** 계정 선택 (사업자 X)
4. **이름**: 본명 (Play 콘솔 내부에서만 보임)
5. **공개 개발자 이름**: `upgul` ← 사용자가 보는 이름. 나중에 변경 가능.
6. **본인 인증** — 신분증 사진 1장 (ID 카드 / 운전면허 / 여권 중 하나) + 셀카 검증
7. **연락처**: 휴대폰 + 이메일
8. **$25 결제** — 카드 1회. 갱신비 없음.
9. 가입 처리 보통 **수 시간 ~ 48시간** 안에 완료됨

가입 처리 끝나면 https://play.google.com/console/u/0/developers/ 에서 새 앱 등록 가능.

---

## 1. 앱 만들기 — Create app

| 필드 | 입력값 |
|---|---|
| App name | `업글 타이머` |
| Default language | `한국어 – ko-KR` |
| App or game | **App** |
| Free or paid | **Free** |
| Declarations | 두 개 모두 체크 ✓ (정책 동의 + 미국 수출법 동의) |

→ **Create app** 누르기

---

## 2. App content (앱 콘텐츠) — 좌측 메뉴 따라가기

### Privacy policy (개인정보처리방침)
```
https://jjaeok-dot.github.io/upgul-timer/privacy.html
```

### App access (앱 접근)
- **All functionality is available without restrictions** 선택
- (로그인 필요한 부분 없음)

### Ads (광고)
- **No, my app does not contain ads** 선택

### Content ratings (콘텐츠 등급) — IARC 설문
- 카테고리: **Reference, News, or Educational** → 또는 **Utility, Productivity, Communication, or Other**
- 폭력/성/약물/도박/공포/언어 모두 **No / Never**
- 결과: **Everyone** (만 4세 이상) 자동 책정

### Target audience and content (대상 연령)
- Target age groups: **18 and over** 가장 안전 (앱이 어린이 대상은 아니지만 부모가 사용)
- (또는 13+ 부터 체크해도 OK)

### News apps
- **No, my app is not a news app**

### Health apps
- **No, my app is not a health app**

### Government apps
- **No, my app is not a government app**

### COVID-19 contact tracing
- **No, my app is not a contact tracing app**

### Data safety (데이터 안전) ⚠️ 가장 중요 — 정직하게 채워야 함
- Does your app collect or share any of the required user data types? → **No**
- Is all of the user data collected by your app encrypted in transit? → **N/A** (수집 0)
- Do you provide a way for users to request that their data is deleted? → **N/A** (수집 0)
- 카테고리별로 모두 "Not collected" 체크

### Government / Financial / Restricted permissions
- 모두 **No / Not applicable**

### Permissions declarations — `SYSTEM_ALERT_WINDOW` 와 `FOREGROUND_SERVICE_SPECIAL_USE`
이건 좀 신경써서 적어야 합니다. 칸이 보이면 아래 텍스트 그대로 입력:

**SYSTEM_ALERT_WINDOW (다른 앱 위에 표시) 사용 이유**:
```
The core feature of this app is to display a small floating timer on top of other apps. Users explicitly enable the overlay permission inside the app settings; the overlay only shows the user-configured countdown values and does not display any other content. Without this permission, the app's primary purpose (a visible-while-using-other-apps timer) cannot function.
```

**FOREGROUND_SERVICE_SPECIAL_USE 사용 이유**:
```
The app runs a foreground service to keep the visual timer accurate while the user is using other apps in the foreground. The user is always notified by a persistent notification while the service is active. The service has no network access and does not collect any data — it only updates the on-screen timer view at 250ms intervals and triggers two local audio alerts (partial cycle reminder, total time end). The user can stop the service from the app or by dismissing the notification.
```

---

## 3. Store listing (스토어 등록정보)

### App icon
- 파일: `icon-512.png` (512 × 512 PNG, 32-bit, alpha 가능)
- 같은 폴더에 다운로드되어 있음

### Feature graphic (피처 그래픽)
- 파일: `feature-1024x500.png` (1024 × 500 PNG, JPG도 OK)
- 폴더 안에 받아둔 1024×500짜리 사용 (Galaxy용 1280×720 아님)

### App screenshots
- 받아둔 4장 사용 (1080 × 2340 PNG)
- `screenshot-1-bubble.png` / `screenshot-2-cycles.png` / `screenshot-3-settings.png` / `screenshot-4-silence.png`
- Play는 최소 2장, 최대 8장. 4장이면 충분.

### Short description (80자 이내)
```
유튜브·게임 위에 떠 있는 동그라미로 사용 시간을 한눈에 보는 오버레이 타이머
```

### Full description (4000자 이내)
```
시간을 주도하는 사람을 위한 오버레이 타이머

업글 타이머는 화면 어떤 앱 위에든 떠 있는 작은 동그라미 타이머입니다. 유튜브를 보든, 게임을 하든, 책을 읽든 — 사용한 시간을 잊지 않게 도와줍니다.

■ 핵심 기능
• 화면 어디든 떠 있는 작은 동그라미 (드래그로 위치 자유)
• 전체 시간 + 부분 시간 동시 표시 (예: 30분 안에 10분마다 알람)
• 부분 알람은 설정한 주기마다 전체 시간 끝까지 자동 반복
• 다이얼 위 노란 점이 다음 알람 위치를 미리 보여줌
• 부분 알람(가벼운 차임) / 최종 알람(묵직한 경보) 두 톤이 분명히 다름
• 알람 울릴 때 동그라미 한 번 누르면 즉시 멈춤
• 어두운 테마와 깔끔한 카드형 설정 화면

■ 이런 분들께
• 유튜브 / 게임 시간을 스스로 조절하고 싶은 분
• 자녀의 시청 시간을 옆에서 같이 보고 싶은 부모
• 포모도로(25-5분) 같은 시간 인터벌로 작업하는 분
• 운동 / 명상 / 단기 집중에 리듬을 잡고 싶은 분

■ 조작법
• 동그라미 한 번 누르기 = 시작 / 정지
• 드래그 = 위치 옮기기
• 길게 누르기 = 설정 화면으로 돌아가기
• 알람 중 한 번 누르기 = 알람 즉시 끔

■ 데이터 / 권한
이 앱은 어떤 개인정보도 수집·저장·전송하지 않습니다. 광고 SDK, 분석 SDK 등 외부 라이브러리도 포함되지 않습니다. 인터넷도 사용하지 않습니다. 단순히 시간 관리를 돕는 도구입니다.

"다른 앱 위에 표시" 권한은 동그라미 타이머를 화면에 띄우기 위해, "포그라운드 서비스" 권한은 타이머가 백그라운드에서도 정확히 동작하도록 유지하기 위해 사용됩니다.

■ 주의
이 앱은 유튜브 등 다른 앱을 차단하지 않습니다. 사용 시간을 시각적으로 보여주는 보조 도구입니다. 차단이 필요하면 갤럭시의 자녀 보호 / 디지털 웰빙 / Family Link를 함께 사용하세요.

만든이: upgul
```

### App category
- **Category**: Productivity
- **Tags** (옵션, 5개까지): `Productivity tools`, `Time management`, `Focus`, `Pomodoro`, `Parenting tools`

### Contact details
- Email: `jjaeok@gmail.com`
- Phone: 본인 휴대폰 (선택)
- Website: `https://jjaeok-dot.github.io/upgul-timer/` (선택)

### External marketing
- 그대로 두기 (Google이 Play Store 외부에서 광고하는 거 허용/거부, 기본값 OK)

---

## 4. Closed testing (클로즈드 테스트) ← 우리가 사용할 트랙

좌측 메뉴 → **Testing** → **Closed testing** 클릭 → **Create track** 또는 기본 "alpha" 트랙 사용

### Track name
- 기본 "Alpha" 그대로 OK
- 또는 사용자 지정 이름 (예: "Family")

### Tester list — Email list
- "Create email list" → 새 리스트 만들기
  - 이름: `Family and friends`
  - 테스터 이메일: 가족/친구 Gmail 주소 한 줄에 하나씩 (Gmail 또는 Google 계정 필수)
- 일단 **사장님 본인 이메일**만 넣고 시작해도 됨. 나중에 추가 가능.

### Opt-in URL
- Closed testing 트랙 만들면 자동 생성됨
- 이 URL을 가족/친구한테 카톡으로 보내면 → 그 사람들이 "Become a tester" 누르고 → Play 스토어에서 정상 설치 가능

### App release — AAB 업로드
- 같은 폴더에 `app-release.aab` 받아둠 (CI 빌드 결과물)
- 업로드 → 자동으로 서명 검증 → 다음 단계
- 첫 업로드면 "Play App Signing" 가입 안내가 나올 수 있음 → **Use Play App Signing** 선택 (Google이 키 관리)

### Release name
```
2.0.0 (9)
```

### Release notes (한국어)
```
첫 클로즈드 테스트 릴리스

• 화면 위에 떠 있는 동그라미 타이머
• 전체 + 부분 시간 동시 표시 + 자동 반복 알람
• 다이얼에 부분 알람 위치 시각화 (노란 점)
• 알람 두 종류 (가벼운 차임 / 묵직한 경보)
• 알람 중 동그라미 탭으로 즉시 끄기
```

### Save → Review release → Start rollout to alpha

검수에 보통 **1~3일** 걸림. 거절되면 메일로 사유 옴 → 수정 후 재제출.

---

## 5. 검수 통과 후 — 테스터에게 공유

### 옵트인 URL을 카톡/문자로 보내면 끝
```
업글 타이머 클로즈드 테스트에 초대합니다 🎯

아래 링크 누르고 "Become a tester" → "Download it on Google Play" → Play 스토어에서 설치하세요.

[Play Console에서 자동 생성된 옵트인 URL]

* 처음 한 번만 "테스터로 등록"하면 됩니다.
* 어떤 보안 설정도 안 건드려도 됩니다 (Play 스토어에서 정상 설치)
```

받는 사람 입장:
1. 링크 누르기
2. "Become a tester" 클릭
3. "Download it on Google Play"
4. 처음 등록 후엔 일반 앱처럼 Play 스토어에서 자동 업데이트도 됨

---

## 6. 자주 막히는 부분 / 주의사항

### 본인 인증
- 신분증 사진은 흐림/잘림/그림자 NG. 햇빛 들어오는 데서 깨끗하게 찍기.
- 셀카는 손가락 가리기 X.
- 24~48시간 처리. 거절되면 다른 신분증으로 재시도.

### 첫 업로드 검수
- "App is using overlay permission" 같은 추가 질문이 나올 수 있음 → 위 권한 정당성 텍스트 복붙
- "Foreground service type 누락" 경고 → 우리는 `specialUse` 명시했으니 OK
- 거절은 흔함. 사유 따라 수정 → 재제출 (보통 30분~1시간 작업)

### 패키지명 충돌
- `kr.upgul.timer` 가 누군가 이미 등록했다면 충돌. 매우 드문 케이스지만 발생 시 패키지명 변경 필요.

### 결제
- $25는 결제 1회. **연 갱신 비용 없음.**
- 환불 기간 30일 (단, Play 정책 위반 사유로 계정 정지되면 환불 안 됨)

### Closed testing 트랙은 영구 사용 가능
- 14일 / 20명 룰은 **프로덕션 승격**에만 적용. 클로즈드 트랙은 영원히 100명까지 사용 가능.
- 가족/지인 위주 운영이면 프로덕션 안 가도 충분.
