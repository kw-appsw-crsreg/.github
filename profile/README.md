# 📖 광운대학교 수강신청 클라이언트-서버 프로젝트

<img src="https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white"> <img src="https://img.shields.io/badge/.Net-512BD4?style=flat-square&logo=dotnet&logoColor=white"> <img src="https://img.shields.io/badge/Visual Studio-5C2D91?style=flat-square&logo=visualstudio&logoColor=white">

![df1](https://github.com/kw-appsw-crsreg/.github/assets/113542209/8f5c59ae-807b-4dec-b39e-505b9a3579ef)




<br>

## ✅ The Goal Of Project
매 학기마다 모든 학생들은 수강신청 프로그램을 통해 자신이 원하는 수업을 신청합니다. 

신입생들은 수강신청을 처음 경험하는 것이기 때문에 생소함을 느낄 수 도 있고 재학생들 또한 수강신청을 미리 준비하고 싶을 수 있습니다. 

저희는 이런 불편함을 고려해 재학생들이 수강신청을 미리 연습하거나 신입생들이 수강프로그램이 어떻게 돌아가는지 알고싶을 때 사용할 수 있도록 최대한 본래 프로그램가 유사하게 구현하여 간편하게 이용해 볼 수 있도록 하는 것이 목표입니다.

## ✅ Programs's Feature
- 수강신청 기능 (과목번호로 서버에 신청요청 → 서버가 응답 : 신청됐는지 아닌지)
- 수강신청 불가능하다면, 그 사유를 사용자에게 표출(인원초과/만석입니다/시간겹침/학점초과)
- 수강삭제 기능
- 학번과 비밀번호로 로그인
- 서버에 연결할 수 없다면 연결불가 응답 표출

![12](https://github.com/kw-appsw-crsreg/.github/assets/113542209/badfc4f9-ca82-46f4-bb2f-d87f2d9fe34d)



<br> 


## ⚒️ Tech. Stack
**C#** 

- WinForm으로 작성하여 우리 학교 수강신청 프로그램과 유사한 기능과 UI 제공

- 네트워크 기술 : 소켓 통신 사용

<서버 프로그램과 클라이언트 프로그램이 소켓으로 정보를 주고받음>

**MariaDb**
- 외부 라이브러리-데이터베이스(MariaDB)

수강신청에 필요한 정보들을 데이터베이스에 저장하고, 이를 프로그램에서 사용하려면 데이터베이스 연동이 필요함

데이터베이스에는 (해당학기 개설과목/학생에 대한 정보/장바구니 정보/수강 정보)를 각각 담은 4개의 메인 테이블과, 참조용 성적/학과 테이블이 존재

## 🖥️ How To Set Up?

### [Client](https://github.com/kw-appsw-crsreg/client)

> A visual studio installation is required before the program can run. Please check [here](https://visualstudio.microsoft.com/ko/downloads/) to install **Visual studio 2022.**

### 1. Git clone
```shell
git clone https://github.com/kw-appsw-crsreg/client

```

### [Server](https://github.com/kw-appsw-crsreg/server)

### 1. Git clone
```shell
git clone https://github.com/kw-appsw-crsreg/server

```

## 🧑‍🤝‍🧑🧑‍🤝‍🧑 Project Members

 <div align="center">
  
  ### 🐔 만석입니다 🐔

|<img src="https://avatars.githubusercontent.com/u/28249968?v=4" width="80">|<img src="https://avatars.githubusercontent.com/u/64678476?v=4" width="80">|<img src ="https://avatars.githubusercontent.com/u/113542209?v=4" width="80">|<img src="https://avatars.githubusercontent.com/u/112372174?v=4" width="80">|
|:---:|:---:|:---:|:---:|
|[42_jaemkim](https://github.com/andrew00874)|[GYUTAE PARK](https://github.com/doraemon500)|[bjPark98](https://github.com/bjPark98)|[yunasin](https://github.com/star1502)|
|Client - Main | Server | Clinet -Login | **Team Leader**<br>Database|
  
   </div>
  
  <br>

## 🧾 License
  README.md of this project originally from [oss-talkative](https://github.com/oss-talkative/.github) project.
