# SQL_otus_HW


Database: otusHW

-- DROP DATABASE IF EXISTS "otusHW";

 CREATE DATABASE "otusHW"
     WITH 
     OWNER = postgres
    ENCODING = 'UTF8'
LC_COLLATE = 'Russian_Russia.1251'
    LC_CTYPE = 'Russian_Russia.1251'
     TABLESPACE = pg_default
    CONNECTION LIMIT = -1;
	
CREATE TABLE questions 
 (
	question_id SERIAL primary key,
	value VARCHAR(100) NOT NULL UNIQUE
	);
SELECT * FROM questions;
SELECT question_id, value FROM questions;

INSERT INTO questions(value)
VALUES ('В каком году умер Виктор цой?')

INSERT INTO questions(value)
VALUES ('В каком году умер Александр Пушкин?');

CREATE TABLE answers
(
	answer_id SERIAL PRIMARY KEY,
	value VARCHAR(100) NOT NULL,
	qustion_id INTEGER REFERENCES questions (question_id)
)

ALTER TABLE answers ADD COLUMN isright boolean;
SELECT * FROM answers;
INSERT INTO answers(value,qustion_id,isright)VALUES
('1)1990',1,true),
('2)1992',1,false),
('3)1994',1,false);

INSERT INTO answers(value,qustion_id,isright)VALUES
('1)1834',2,false),
('2)1837',2,true),
('3)1845',2,false);
