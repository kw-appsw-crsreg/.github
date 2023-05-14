# 📖 광운대학교 수강신청 프로그램 

<img src="https://img.shields.io/badge/-MariDB-lightgrey"><img src="https://img.shields.io/badge/-C%23-blue">

<br>

## ✅ The Goal Of Project
매 학기마다 모든 학생들이 사용하는 수강 신청 프로그램을 실제로 구현하면서 C#의 다양한 활용을 학습하고 더 나아가 실질적인 목적으로 사용되고 있는 프로그램을 직접 구현함으로서 프로그래머로서의 역량을 늘리는 것

## ✅ Programs's Option
- 수강신청 기능 (과목번호로 서버에 신청요청 → 서버가 응답 : 신청됐는지 아닌지)
- 수강신청 불가능하다면, 그 사유를 사용자에게 표출(인원초과/만석입니다/시간겹침
/학점초과)
- 수강삭제 기능
- 학번과 비밀번호로 로그인
- 서버에 연결할 수 없다면 연결불가 응답 표출

<br> 


## ⚒️ Program's Tool
**C#** 

- WinForm으로 작성하여 우리 학교 수강신청 프로그램과 유사한 기능과 UI 제공

- 네트워크 기술 : 소켓 통신 사용

<서버 프로그램과 클라이언트 프로그램이 소켓으로 정보를 주고받음>

**MariaDb**
- 외부 라이브러리-데이터베이스(MariaDB)

수강신청에 필요한 정보들을 데이터베이스에 저장하고, 이를 프로그램에서 사용하려면 데이터베이스 연동이 필요함

데이터베이스에는 (해당학기 개설과목/학생에 대한 정보/장바구니 정보/수강 정보)를 각각 담은 4개의 테이블이 존재함

## 🖥️ How To Set Up?

### [Client](https://github.com/kw-appsw-crsreg/client)

> A visual studio installation is required before the program can run. Please check [here](https://visualstudio.microsoft.com/ko/downloads/) to install **Visual studio 2022.**

### 1. Git clone
```shell
git clone https://github.com/kw-appsw-crsreg/client
```

## 🧑‍🤝‍🧑🧑‍🤝‍🧑 Project Member


|<img src="https://avatars.githubusercontent.com/u/28249968?v=4" width="80">|<img src="https://avatars.githubusercontent.com/u/64678476?v=4" width="80">|<img src ="https://avatars.githubusercontent.com/u/113542209?v=4" width="80">|<img src="https://avatars.githubusercontent.com/u/112372174?v=4" width="80">|
|:---:|:---:|:---:|:---:|
|[42_jaemkim](https://github.com/andrew00874)|[GYUTAE PARK](https://github.com/doraemon500)|[bjPark98](https://github.com/bjPark98)|[yunasin](https://github.com/star1502)|
|Client - Main | Server | Cline-Login | **Team Leader**<br>Database|
