# 📖 광운대학교 수강신청 클라이언트-서버 프로젝트

<img src="https://img.shields.io/badge/MariaDB-003545?style=flat-square&logo=mariadb&logoColor=white"> <img src="https://img.shields.io/badge/.Net-512BD4?style=flat-square&logo=dotnet&logoColor=white"> <img src="https://img.shields.io/badge/Visual Studio-5C2D91?style=flat-square&logo=visualstudio&logoColor=white">

![df1](https://github.com/kw-appsw-crsreg/.github/assets/113542209/8f5c59ae-807b-4dec-b39e-505b9a3579ef)




<br>

## ✅ Why This Project?
- 응용소프트웨어실습 교과목에서 배우는 WinForm C#, 소켓 통신을 활용해 보기 위함
- 수강신청 프로그램은 클라이언트와 서버로 구성되며, 이 둘을 연결하는 소켓 통신의 패킷을 구현해 보기 위함
- SQL 질의문을 직접 작성하고, 관계형 데이터베이스를 실제로 설계하여 사용해 보기 위함
- 팀 프로젝트에서 서로 협업하는 경험을 가져 보기 위함

## ✅ Programs's Feature
- 학번과 비밀번호로 로그인
- 서버에 연결할 수 없다면 연결불가 응답 표출
- 실제 광운대학교 수강신청 프로그램과 유사한 기능, UI 제공
- 수강 신청하기 (학정번호와 학번 서버에 전송 → 서버가 응답 : 신청가능 or NOT)
- 수강신청 불가능하다면, 그 사유를 사용자에게 표출(인원초과/만석입니다/시간겹침/학점초과)
- 수강삭제
- 과목 즐겨찾기

![12](https://github.com/kw-appsw-crsreg/.github/assets/113542209/badfc4f9-ca82-46f4-bb2f-d87f2d9fe34d)



<br> 


## ⚒️ Tech. Stack
**C#** 
- WinForm으로 작성하여 우리 학교 수강신청 프로그램과 유사한 기능과 UI 제공
- 소켓 통신, 패킷 통신
 - 서버 프로그램과 클라이언트 프로그램이 소켓으로 정보를 주고받음

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
|Client - Main | Server-Socket/Packet | Clinet -Login | **Team Leader**<br>Server-Database|
  
   </div>
  
  <br>

## 🧾 License
  README.md of this project originally from [oss-talkative](https://github.com/oss-talkative/.github) project.

## 🛢 Database Structure
```SQL
-- --------------------------------------------------------
-- 호스트:                          127.0.0.1
-- 서버 버전:                        10.9.5-MariaDB - mariadb.org binary distribution
-- 서버 OS:                        Win64
-- HeidiSQL 버전:                  11.3.0.6295
-- --------------------------------------------------------

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET NAMES utf8 */;
/*!50503 SET NAMES utf8mb4 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


-- sugang 데이터베이스 구조 내보내기
CREATE DATABASE IF NOT EXISTS `sugang` /*!40100 DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci */;
USE `sugang`;

-- 테이블 sugang.opened_course 구조 내보내기
CREATE TABLE IF NOT EXISTS `opened_course` (
  `year` year(4) NOT NULL,
  `semester` tinyint(1) unsigned NOT NULL,
  `department` char(4) NOT NULL COMMENT '개설단과대/학과',
  `level` tinyint(1) unsigned NOT NULL COMMENT '난이도/학년',
  `subject` char(4) NOT NULL COMMENT '과목번호',
  `class` int(2) NOT NULL COMMENT '분반',
  `course_id` char(16) NOT NULL DEFAULT concat(`year`,`semester`,`department`,`level`,`subject`,lpad(`class`,2,'0')) COMMENT '강의 고유값',
  `type` varchar(5) NOT NULL COMMENT '이수구분(교선,전필등)',
  `course_name` varchar(50) NOT NULL COMMENT '과목명',
  `credit` tinyint(3) unsigned NOT NULL DEFAULT 3 COMMENT '학점',
  `instructor_name` varchar(20) NOT NULL DEFAULT '미지정',
  `num_of_students` smallint(5) unsigned NOT NULL DEFAULT 0 COMMENT '현재수강인원',
  `remaining_capacity` smallint(5) unsigned NOT NULL COMMENT '여석',
  `time` varchar(50) NOT NULL DEFAULT '미지정' COMMENT '강의교시',
  `lect_room` varchar(50) NOT NULL DEFAULT '미지정',
  `is_foreignerOnly` tinyint(1) NOT NULL DEFAULT 0 COMMENT '외국인전용인가?',
  PRIMARY KEY (`course_id`) USING BTREE,
  CONSTRAINT `CC1` CHECK (`remaining_capacity` >= 0)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci COMMENT='List of opened course for this semester';

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.reference_department 구조 내보내기
CREATE TABLE IF NOT EXISTS `reference_department` (
  `department` char(4) NOT NULL DEFAULT '',
  `department_str` varchar(20) NOT NULL COMMENT '학과',
  `college_of` varchar(20) NOT NULL COMMENT '단과대',
  PRIMARY KEY (`department`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.reference_grade 구조 내보내기
CREATE TABLE IF NOT EXISTS `reference_grade` (
  `grade` char(2) NOT NULL,
  `gpa` float DEFAULT NULL,
  PRIMARY KEY (`grade`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci COMMENT='성적 환산';

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.registerd_favorites 구조 내보내기
CREATE TABLE IF NOT EXISTS `registerd_favorites` (
  `student_id` varchar(20) NOT NULL,
  `idx` tinyint(3) unsigned NOT NULL DEFAULT 0 COMMENT '몇번째즐겨찾기인지',
  `course_id` char(16) NOT NULL DEFAULT '0',
  PRIMARY KEY (`student_id`,`idx`),
  KEY `st_id` (`student_id`) USING BTREE,
  KEY `courseid` (`course_id`),
  CONSTRAINT `courseid` FOREIGN KEY (`course_id`) REFERENCES `opened_course` (`course_id`) ON DELETE CASCADE ON UPDATE CASCADE,
  CONSTRAINT `studentid` FOREIGN KEY (`student_id`) REFERENCES `student_info` (`student_id`) ON DELETE NO ACTION ON UPDATE NO ACTION
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci COMMENT='List of Added Favorites';

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.same_subject 구조 내보내기
CREATE TABLE IF NOT EXISTS `same_subject` (
  `subject` char(4) NOT NULL DEFAULT '',
  `same_subject` char(4) NOT NULL DEFAULT ''
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.student_info 구조 내보내기
CREATE TABLE IF NOT EXISTS `student_info` (
  `student_id` varchar(20) NOT NULL DEFAULT '',
  `name` text NOT NULL,
  `password` text NOT NULL,
  `college_of` varchar(20) NOT NULL COMMENT '단과대',
  `department_str` varchar(20) NOT NULL COMMENT '학과/학부',
  `is_foreigner` tinyint(1) NOT NULL DEFAULT 0,
  `max_credit` int(11) unsigned NOT NULL DEFAULT 19,
  `registered_credit` int(11) unsigned NOT NULL DEFAULT 0,
  `registered_times` varchar(250) NOT NULL DEFAULT '' COMMENT '등록된시간',
  PRIMARY KEY (`student_id`),
  CONSTRAINT `CC1` CHECK (`registered_credit` <= `max_credit`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 테이블 sugang.takes_info 구조 내보내기
CREATE TABLE IF NOT EXISTS `takes_info` (
  `student_id` varchar(20) NOT NULL DEFAULT '',
  `course_id` char(16) NOT NULL,
  `type` varchar(5) DEFAULT NULL,
  `grade` char(2) DEFAULT NULL COMMENT '성적',
  KEY `FK_takes_info_opened_course` (`course_id`),
  KEY `FK_takes_info_student_info` (`student_id`),
  CONSTRAINT `FK_takes_info_opened_course` FOREIGN KEY (`course_id`) REFERENCES `opened_course` (`course_id`) ON DELETE NO ACTION ON UPDATE NO ACTION,
  CONSTRAINT `FK_takes_info_student_info` FOREIGN KEY (`student_id`) REFERENCES `student_info` (`student_id`) ON DELETE CASCADE ON UPDATE CASCADE
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- 내보낼 데이터가 선택되어 있지 않습니다.

-- 트리거 sugang.takes_info_after_delete 구조 내보내기
SET @OLDTMP_SQL_MODE=@@SQL_MODE, SQL_MODE='STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
DELIMITER //
CREATE TRIGGER `takes_info_after_delete` AFTER DELETE ON `takes_info` FOR EACH ROW BEGIN
-- 잔여석 업데이트
UPDATE opened_course SET remaining_capacity=remaining_capacity+1, num_of_students=num_of_students-1 WHERE OLD.course_id=course_id;
-- 학생 수강학점 업데이트
UPDATE student_info,
(SELECT credit, YEAR, semester FROM opened_course WHERE opened_course.course_id=OLD.course_id) AS tmp
SET student_info.registered_credit=student_info.registered_credit-tmp.credit
WHERE student_info.student_id=OLD.student_id AND tmp.YEAR=year(CURDATE()) AND tmp.semester=1;

-- 학생 수강신청한 시간 업데이트
if (SELECT `time` FROM opened_course WHERE course_id=OLD.course_id ) != '미지정' then
UPDATE student_info,
(SELECT `time`, `year` FROM opened_course WHERE opened_course.course_id=OLD.course_id) AS tmp
SET registered_times=REPLACE(registered_times, tmp.`time`, '' )
WHERE student_info.student_id=OLD.student_id;
END if;

END//
DELIMITER ;
SET SQL_MODE=@OLDTMP_SQL_MODE;

-- 트리거 sugang.takes_info_after_insert 구조 내보내기
SET @OLDTMP_SQL_MODE=@@SQL_MODE, SQL_MODE='STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
DELIMITER //
CREATE TRIGGER `takes_info_after_insert` AFTER INSERT ON `takes_info` FOR EACH ROW BEGIN
-- 잔여석 업데이트
UPDATE opened_course SET remaining_capacity=remaining_capacity-1,num_of_students=num_of_students+1 WHERE NEW.course_id=course_id;
-- IF (SELECT department_str FROM student_info WHERE student_info.student_id=takes_info.student_id)!=(SELECT )
-- 학생 수강학점 업데이트
UPDATE student_info,
(SELECT credit,YEAR,semester FROM opened_course WHERE opened_course.course_id=NEW.course_id) AS tmp
SET student_info.registered_credit=student_info.registered_credit+tmp.credit
WHERE student_info.student_id=NEW.student_id AND tmp.YEAR=year(CURDATE()) AND tmp.semester=1;
-- 학생 수강신청한 시간 업데이트
-- UPDATE student_info,
-- (SELECT `time`, `year` FROM opened_course WHERE opened_course.course_id=NEW.course_id) AS tmp
-- SET registered_times=CONCAT(registered_times, tmp.`time` )
-- WHERE student_info.student_id=NEW.student_id;

-- 학생 수강신청한 시간 업데이트
if (SELECT `time` FROM opened_course WHERE course_id=NEW.course_id ) != '미지정' then
UPDATE student_info,
(SELECT `time`, `year` FROM opened_course WHERE opened_course.course_id=NEW.course_id) AS tmp
SET registered_times=CONCAT(registered_times, tmp.`time` )
WHERE student_info.student_id=NEW.student_id;
END if;

END//
DELIMITER ;
SET SQL_MODE=@OLDTMP_SQL_MODE;

-- 트리거 sugang.takes_info_after_update 구조 내보내기
SET @OLDTMP_SQL_MODE=@@SQL_MODE, SQL_MODE='STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';
DELIMITER //
CREATE TRIGGER `takes_info_after_update` AFTER UPDATE ON `takes_info` FOR EACH ROW BEGIN
if OLD.course_id != NEW.course_id then
 UPDATE opened_course SET remaining_capacity=remaining_capacity+1,num_of_students=num_of_students-1 WHERE OLD.course_id=course_id;
 UPDATE opened_course SET remaining_capacity=remaining_capacity-1,num_of_students=num_of_students+1 WHERE NEW.course_id=course_id;
 END if;
END//
DELIMITER ;
SET SQL_MODE=@OLDTMP_SQL_MODE;

/*!40101 SET SQL_MODE=IFNULL(@OLD_SQL_MODE, '') */;
/*!40014 SET FOREIGN_KEY_CHECKS=IFNULL(@OLD_FOREIGN_KEY_CHECKS, 1) */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40111 SET SQL_NOTES=IFNULL(@OLD_SQL_NOTES, 1) */;

```
