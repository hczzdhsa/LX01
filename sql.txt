DROP DATABASE IF EXISTS Works;
CREATE DATABASE Works DEFAULT CHARSET=GBK;

USE Works;
CREATE TABLE UserInfo
(
UserName nvarchar(50) Primary key,
Password nvarchar(50) not null,
QQ nvarchar(12),
Email nvarchar(50),
Type nchar(10) not null,
UserImg nvarchar(250)
);

CREATE TABLE Activity
(
ActivityID int(4) Primary KEY auto_increment,
ActivitName nvarchar(125) not null,
EndTime datetime(6) not null,
ActivityPicture nvarchar(250) not null,
ActivityIntroduction nvarchar(8000),
Summary nvarchar (250),
ActivityVerify nchar(10) not null DEFAULT '¡äy¨¦¨®o?',
ActivityStatus nchar(10),
UserName nvarchar(50) not null
);

CREATE TABLE WorkInfo
(
WorkID int(4) Primary KEY,
WorkName nvarchar(50) not null,
WorkPicture nvarchar(250) not null,
UploadTime datetime(6) not null,
WorkIntroduction nvarchar(8000),
WorkVerify nchar(10) not NULL DEFAULT '¡äy¨¦¨®o?',
UserName nvarchar(50) not null,
ActivityName nvarchar(125),
Recommend nchar(2) not null,
RecommendTime dateTime(6)
);

CREATE TABLE Commeut
(
CommentID int(4) PRIMARY KEY auto_increment,
WordID int(4) not null,
WordName nvarchar(50) not null,
UserName nvarchar(50) not null,
CommentContent nvarchar(8000) not null,
CommentTime dateTime(6) not null
);

CREATE TABLE Image
(
ImgID int(4) PRIMARY KEY auto_increment,
ImgUrl nvarchar(50) not null,
ImgText nvarchar(50) not null,
ImgLink nvarchar(100) not null,
ImgAlt nvarchar(50) not null
);

ALTER TABLE WorkInfo
ADD FOREIGN KEY(UserName) REFERENCES UserInfo(UserName);

ALTER TABLE Commeut
ADD FOREIGN KEY(UserName) REFERENCES WorkInfo(UserName);

ALTER TABLE Commeut
ADD FOREIGN KEY(UserName) REFERENCES UserInfo(UserName);

ALTER TABLE Activity
ADD FOREIGN KEY(UserName) REFERENCES UserInfo(UserName);