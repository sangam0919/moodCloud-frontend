### 📚 목차
 팀원 소개 및 역할

 프로젝트 소개

 기술 스택

 api 문서 

 팀 전체 회고

 다음 프로젝트에 적용할 점

 My 작업 리스트

 최종 후기



##  Mood Cloud 프로젝트 회고록

###  팀원 소개 및 역할

| 이름 | 역할 | 주요 담당 업무 |
|------|------|----------------|
| 김지은 (팀장) | 프로젝트 기획 / 앱 프론트엔드 / 앱 백엔드 | 전체 기획, 앱 화면 구성 및 기능 구현 |
| 이상암 | 웹 프론트엔드 / 웹 백엔드 | 로그인 페이지, 메인 페이지, 수정 페이지, 글쓰기 페이지, 글 상세 페이지, 마이페이지 |
| 구다경 | 웹 프론트엔드 / 웹 백엔드 | 리스트 페이지, 내 정보 수정 페이지, 통계 페이지 |

---
###  프로젝트 소개

사람들은 자신의 감정을 말로 표현하거나 객관적으로 바라보는 데 익숙지 않습니다.  
하루를 살아내는 데 집중하다 보면 감정은 흘러보내기 쉽고,  
그러다 보면 스스로의 마음을 놓치게 됩니다.  
**Mood Cloud**는 이러한 사용자를 위해 AI가 일기 내용을 분석해 몰랐던 나의 감정까지 발견할 수 있도록 도와주며,  
감정의 흐름을 시각적으로 확인할 수 있어 나를 더 깊이 이해할 수 있게 합니다.  
또한 감정을 기반으로 친구들과 감정을 공유하고 공감하는 커뮤니케이션을 경험할 수 있어,  
타인의 감정도 헤아릴 수 있는 공간을 제공합니다.

---

### 🛠 기술 스택
## 프론트엔드
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=JavaScript&logoColor=black)
![React](https://img.shields.io/badge/React-61DAFB?style=flat&logo=React&logoColor=white)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=flat&logo=react&logoColor=61DAFB)
![Redux](https://img.shields.io/badge/Redux-764ABC?style=flat&logo=Redux&logoColor=white)
![Styled Components](https://img.shields.io/badge/styled--components-DB7093?style=flat&logo=styled-components&logoColor=white)
![Toast UI Editor](https://img.shields.io/badge/Toast_UI_Editor-0097E0?style=flat)
## 백엔드
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=Node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-000000?style=flat&logo=express&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat&logo=MySQL&logoColor=white)

## 협업툴 및 라이브러리
![OpenAI API](https://img.shields.io/badge/OpenAI_API-412991?style=flat&logo=openai&logoColor=white)
![Kakao Login](https://img.shields.io/badge/Kakao_Login-FFCD00?style=flat&logo=KakaoTalk&logoColor=black)
![Notion](https://img.shields.io/badge/Notion-000000?style=flat&logo=Notion&logoColor=white)
![Discord](https://img.shields.io/badge/Discord-5865F2?style=flat&logo=discord&logoColor=white)
---

#  감정 기반 일기 플랫폼 API 문서

이 프로젝트는 감정 분석 기반의 일기 작성, 팔로우, 통계, 카카오 로그인 등을 포함한 **Express.js 기반 백엔드 API**입니다.  
웹과 앱에서 모두 사용할 수 있도록 엔드포인트를 분리하여 제공합니다.

---

##  공통 안내

- 인증 방식  
  - 웹: `authMiddleware` (JWT 쿠키)
  - 앱: `authAppMiddleware` (Authorization 헤더에 토큰)

- 업로드 경로  
  - 이미지: `/upload` (form-data)

---

##  Diary (일기)

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/diary/:id` | 특정 일기 상세 조회 |
| `GET` | `/diary/:id/edit` | 일기 수정을 위한 데이터 조회 |
| `POST` | `/diary` | (앱) 일기 생성 |
| `POST` | `/diary/app` | (앱) 일기 생성 |
| `PUT` | `/diary/:id` | 일기 수정 |
| `PUT` | `/diary/app/:id` | (앱) 일기 수정 |
| `DELETE` | `/diary/delete/:id` | 일기 삭제 |
| `GET` | `/main/mydiary` | 최근 일기 목록 (웹) |
| `GET` | `/main/app/mydiary` | 전체 일기 목록 (앱) |
| `GET` | `/main/diary/followed` | 팔로우한 사람들의 일기 (웹) |
| `GET` | `/main/app/diary/followed` | 팔로우한 사람들의 일기 (앱) |
| `GET` | `/public/:uid` | 특정 유저의 공개 일기 |

---

##  Comment (댓글)

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `POST` | `/diary/createComment` | 댓글 작성 (웹) |
| `POST` | `/diary/app/createComment` | 댓글 작성 (앱) |

---

##  Follow (팔로우)

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `POST` | `/follow/create` | 팔로우 생성 |
| `GET` | `/follow/status` | 팔로우 상태 확인 |
| `DELETE` | `/follow/delete` | 팔로우 취소 |
| `GET` | `/follow/app/followers` | 팔로워 목록 (앱) |
| `GET` | `/follow/app/followings` | 팔로잉 목록 (앱) |
| `GET` | `/follow/app/followings/todayDiaries` | 오늘 작성한 팔로우 일기 (앱) |

---

##  Emotion (감정)

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/main/emotionAll` | 감정 전체 조회 |
| `POST` | `/main/emotionOnly` | 감정만 기록 (웹) |
| `POST` | `/main/app/emotionOnly` | 감정만 기록 (앱) |
| `POST` | `/diary/analyze` | AI 감정 분석 (gpt-3.5-turbo 사용) |

---

##  기록 상태

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/main/checkTodayWritten` | 오늘 기록 여부 (웹) |
| `GET` | `/main/app/checkTodayWritten` | 오늘 기록 여부 (앱) |
| `GET` | `/main/app/todayDiary` | 오늘 일기 조회 (앱) |
| `GET` | `/main/app/randomDiary` | 랜덤 일기 조회 (앱) |

---

##  통계

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/main/streak` | 스트릭 조회 (웹) |
| `GET` | `/main/written-weekdays` | 요일별 작성 통계 |
| `GET` | `/main/written-dates` | 월별 작성 날짜 |
| `GET` | `/main/app/streak` | 스트릭 조회 (앱) |
| `GET` | `/main/app/written-dates` | 앱 전용 작성 날짜 |
| `GET` | `/main/app/calendar-emotions` | 감정 달력 데이터 |
| `GET` | `/stats/app/emotion` | 감정 통계 (앱) |
| `GET` | `/stats/app/streak` | 스트릭 통계 (앱) |

---

##  유저 검색

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/search/users?q=닉네임` | 닉네임으로 유저 검색 |
| `GET` | `/login/:id` | 유저 ID로 프로필 조회 |

---

##  유저 프로필

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/settings/me/profile` | 내 프로필 정보 조회 |
| `PATCH` | `/settings/me/bio` | 자기소개 수정 |
| `POST` | `/settings/me/profile-image` | 프로필 이미지 업로드 |
| `GET` | `/settings/delete` | 회원 탈퇴 |
| `GET` | `/settings/lists` | 내 팔로우 목록 |
| `DELETE` | `/settings/:userIdToUnfollow` | 언팔로우 |

---

##  카카오 로그인

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `GET` | `/login/kakao` | 카카오 로그인 URL 반환 |
| `GET` | `/login/kakao_login` | 웹 카카오 로그인 콜백 처리 |
| `POST` | `/login/kakaoapp` | 앱 카카오 로그인 처리 |
| `GET` | `/login/logout` | 로그아웃 처리 |
| `GET` | `/login/user` | 로그인 유저 정보 (웹) |
| `GET` | `/login/app/user` | 로그인 유저 정보 (앱) |

---

## 이미지 업로드

| 메소드 | 엔드포인트 | 설명 |
|--------|------------|------|
| `POST` | `/diary/upload` | 이미지 업로드 (멀터, 파일 URL 반환) |

---

>  이 API 문서는 `Express + JWT + Sequelize + Kakao OAuth + OpenAI` 기반으로 설계되었습니다.  
> 앱과 웹의 인증 방식을 구분하였으며, 가볍고 빠른 감정 일기 플랫폼을 목표로 합니다.



---


### 팀 전체 회고

#### 잘한 점
- 빠른 주제 선정
- 디렉터리 구조를 정리하고 일정관리를 회의를 통해 진행하고 협업툴로 관리하였다. 
- 배포에 이슈를 트래킹하기 위해서 배포를 먼저 진행하고 프로젝트를 작업하였습니다.
#### 아쉬운 점  
- 세심한 폴더 구조관리에 대해서 소통이 원할하지 못했다.

#### 배운 점
- 개인 작업을 할때와 팀 작업을 할때에 디렉토리 구조를 정함에 있어서 소통의 중요성을 알겠되었습니다    
- 프로젝트라는것을 개발을 하면서 항상 사용자 역할만 해봤지만 사용자를 위한 서비스를 생각하는게 어렵다는것을 배웠습니다.  

---

###  다음 프로젝트에 적용할 점
- 더욱 깔끔한 디자인  
- 맡은 기능의 완벽함
- 추가적인 꼭 필요한 기능(임시저장 등)

---


###  my 작업 리스트

<img src="./gif/Honeycam 2025-06-04 13-18-43.gif" width="600">

- **로그인 페이지**  
  카카오로그인으로 로그인을 하지 않으면 메인으로 넘어갈 수 없다.

- **메인 페이지**  
  전반적인 컴포넌트들을 들어갈 수 있는 곳입니다.

- **글쓰기 페이지**  
  글을 쓰는 곳으로 이미지를 넣을 수 있고, 작성하면 AI 검사를 통해 감정을 분석하고  
  공개와 비공개 설정을 할 수 있다.

---

<img src="./gif/Honeycam 2025-06-04 13-21-59.gif" width="600">

- **상세 페이지**  
  작성한 글을 상세하게 볼 수 있고, 수정도 가능하다.  
  또한 팔로우 기능이 있으며, 댓글 작성 기능도 포함되어 있다.

- **수정 페이지**  
  기존 글과 이미지를 수정할 수 있으며, 수정 시 다시 AI 감정 분석을 수행한다.

---

<img src="./gif/Honeycam 2025-06-04 13-25-54.gif" width="600">

- **마이페이지**  
  내가 쓴 글과 스트릭(스트림) 등을 볼 수 있고,  
  다른 사람의 마이페이지에 들어가면 **팔로우 여부에 따라 접근이 다르다**.  

  - 팔로우한 경우: 친구의 공개된 글들을 볼 수 있음  
  - 팔로우하지 않은 경우: 블라인드 처리가 되어 내용을 볼 수 없음  

  다른 사람의 마이페이지에 들어가려면 **검색창에 그 사람의 이름을 입력해야 한다**.
---
### 최종 후기
앱과 웹을 모두 개발하는 과정에서
하나의 백엔드 로직이라도 **기기 환경(모바일 vs. 브라우저)**에 따라 다르게 동작해야 할 상황이 많았고,
이를 처리하기 위해 디바이스 환경을 고려한 분기 처리와 조건 설계의 중요성을 배웠습니다.
이 과정에서 직접 많은 자료를 찾아보며 다양한 플랫폼에 대응하는 백엔드 설계에 대한 이해를 넓힐 수 있었습니다.