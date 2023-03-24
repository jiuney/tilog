---
layout: post
title: SQL Basics
tags: [SQL]
author: h
categories: SQL
---





# SQL Basics

[@freeCodeCamp](https://www.freecodecamp.org/learn/relational-database/)

[Bash basics](https://www.notion.so/Bash-basics-602f9466f4b14137bc05190b1f785d36)

# psql 명령어

# SQL 기초

# bash

# SQL keywords

# SQL join

# # 정리 전

### psql 시작

- bash에서 postgresql 시작
    - `psql --username=<사용자이름> --dbname=<db이름>`
- `\l` : List of databases 출력
- `\c <database>` : 데이터베이스에 연결
- `\d` : List of relations 출력
- 테이블 디테일 보는 법
    - `\d` : List of relations 출력
    - `\d <table>` : 테이블 디테일 출력

### 테이블 기초

- 빈 테이블 생성 : `CREATE TABLE <table>();`
- 테이블 삭제 : `DROP TABLE <table>;`
- 테이블 내용 보기 : `SELECT * FROM <table>;`
- 테이블에 값 넣기
    - `INSERT INTO <테이블명> (<컬럼1>, <컬럼2>, ...) VALUES (<값1>, <값2>, ...);`
        - 모든 열에 다 값을 입력하는 경우에는 컬럼명 입력 생략 가능
    - **※주의※ 겹따옴표 사용하면 에러남. 홑따옴표 사용 필수!**
        - 이상하게 값에 겹따옴표를 쓰면 그 값을 컬럼명으로 인식하는 것 같다. `Column "값" does not exist` 라는 에러가 뜬다.
- 소수점 자료형 표현법
    - float 사용
    - numeric 사용
        - 예) `numeric(2,1)` → 2 digits, 소수점 아래 1 digit

### 제약 조건 넣기

- primary key 설정 : 자료형 다음에 `PRIMARY KEY` 입력
    
    ```sql
    CREATE TABLE citizen(
    	ssn integer PRIMARY KEY, 
    	last_name varchar(40), 
    	first_name varchar(40), 
    	birth_date date
    );
    ```
    
- NOT NULL 제약조건
    - Not Null 추가 : primary key 처럼 자료형 뒤에 작성
        - `ALTER TABLE <table> ALTER COLUMN <column> <datatype> NOT NULL;`
    - Not Null 제거 : Not Null 안쓰고 Alter하면 제거됨.
        - `ALTER TABLE <table> ALTER COLUMN <column> <datatype>;`
- foreign key 설정
    - `ALTER TABLE <바꿀테이블> ADD FOREIGN KEY (<타겟컬럼명>) REFERENCES <참조테이블> (<소스컬럼명>);`
- Composite Primary Key
    - 여러 컬럼을 조합해서 primary key로 사용
    - `ALTER TABLE <테이블명> ADD PRIMARY KEY (<컬럼1>, <컬럼2>);`

### 

### 

### 

### 

### 

# ㅎ

## 참고

[[MySQL] 데이터 추가, 수정, 삭제 (INSERT, UPDATE, DELETE)](http://extbrain.tistory.com/47)

[[TIL] 8일차 TIL(20230215) - DBMS이론 및 SQL기초, 조건절](http://better0.tistory.com/30)

[freeCodeCamp.org](https://www.youtube.com/freecodecamp)

[freeCodeCamp.org](https://www.freecodecamp.org/learn/relational-database/learn-sql-by-building-a-student-database-part-1/build-a-student-database-part-1)

[freeCodeCamp.org](https://www.freecodecamp.org/learn/relational-database/learn-sql-by-building-a-student-database-part-2/build-a-student-database-part-2)

- bash terminal
    - `touch <파일명>.<확장자>` → 파일 생성
    - shebang : `#!` 로 시작하는 문자 시퀀스. 파일의 나머지 부분을 구문분석하는데 사용할 인터프리터를 운영체제에 알려주는데 사용됨.
    - 주석 : `#` 이후의 모든 내용 무시. 단! 같은 줄에 쓰인 내용만. bash는 여러 줄 주석은 지원하지 않음. 모든 주석 줄의 맨 앞에 각 줄마다 `#`을 써야 함.
- bash 내에서 파일 수정 ([참고](https://opentutorials.org/course/730/4561))
    1. `vim <파일명>.<확장자>` → vi 편집기 열림. 처음엔 읽기모드.
    2. 키보드에서 `i` 한글자 입력하면 insert mode가 되어서 내용 편집 가능. 이렇게 내용 편집.
    3. `esc` 누르면 다시 명령어 모드로 바뀜.
    4. 명령어 모드에서 `:w` 입력하고 `Enter` 눌러서 바뀐 내용 저장.
    5. `:q` 입력하고 `Enter` 눌러서 vi 종료.
- 스크립트 실행하는 방법들
    - 그냥 `파일경로/파일명.확장자`
        - 근데 이렇게 하려면 파일에 실행권한 필요. `chmod`로 권한 변경 가능.
    - `sh <파일명>.<확장자>`
    - `bash <파일명>.<확장자>`
- 리눅스 `cat` 명령어에는 여러 기능이 있다. 출력, 병합, 등등. ([참고](https://withcoding.com/109))
- `$` : 변수를 다룰 때 씀.
    - 예) echo $MAJOR → MAJOR라는 변수 출력
- 변수 vs. $변수
    - `변수명=값` 으로 변수를 선언하고, 변수를 사용할 때는 변수명 앞에 `$`를 붙여 사용한다.
    - `${변수}` 와 같이 중괄호로 묶어 쓸 수도 있고, 이렇게 해야만 동작하는 경우도 있다.
        - 예) echo ${string}
- read 명령어
    - input을 받아서 string을 split해서 field(=column)으로 만듦.
    - 즉, 각각의 word를 각 argument에 assign하는 것. 만약 variable(=argument=field) 보다 words가 많으면, 마지막 variable에 남은 단어 모두 assign됨. ([참고](https://phoenixnap.com/kb/bash-read))
- IFS : “Internal Field Separator”. 이름 그대로 separator.
    - 예를 들어, read 명령어를 쓸 때 한 단어씩 split 되는 이유는 default IFS가 공백(space)이기 때문.
- `default -p IFS` : 현재 IFS 보여주는 명령어.
- bash에서는 띄어쓰기가 중요한건가? terminal에서 vim으로 코드 작성할 때, `A = B` 일 때랑 `A=B` 일 때 A의 색깔이 서로 다르다. VSCODE는 color-coded이기 때문에 색이 다른 건 속성이 다르단 뜻일텐데…
- 어려웠던 부분
    
    ```sql
    PSQL="psql -x --username= ...... "
    	......
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR';")
    ```
    
    - 저 코드 마지막에 `‘$MAJOR’` 의 홑따옴표가 매우 중요. 없으면 에러 남. 왜 그럴까?
        - **변수가 문장일 수도 있어서!** 
        예를 들어, MAJOR=”Republic of Korea” 라면
        WHERE major=$MAJOR 는
        WHERE major=Replublic of Korea 이기 때문에
        major=Republic 이 되고, “of” 와 “Korea”는 붕 뜬다.
        - 변수가 문장일 경우, 저렇게 ‘$변수’를 홑따옴표로 자주 감싼다고 한다. (← 아빠가 알려줌!)

### Test & z flag

- z flag
    - bash에서는 `test` 라는 빌트인 커맨드를 지원. 이 명령어로 파일타입이나 값 비교 가능.
    - `test` 대신 `[ ]` 를 쓰기도 함.
        
        ```bash
        test 2 -gt 1 && echo "2 is greater" || echo "1 is greater"
        [ 2 -gt 1 ] && echo "2 is greater" || echo "1 is greater"
        # 위 두 코드는 같은 작업
        ```
        
    - `test` 명령어에서 쓸 수 있는 파라미터 중 하나가 `-z` flag.
    - `-z` flag : a parameter that checks if the length of a variable is zero and returns true if it is zero.
        
        ```bash
        >>> [ -z "" ] && echo "empty" || echo "non-empty"
        empty
        >>> [ -z "test string" ] && echo "empty" || echo "non-empty"
        non-empty
        ```
        
- `[` 와 `[[ (Double square brackets)` 의 차이
    - `[` : POSIX
    - `[[` : Bash extension
        
        > Double `[[]]` are an extension to the standard `[]` and are supported by bash and other shells (e.g. zsh, ksh). They support extra operations (as well as the standard posix operations). For example: `||` instead of `-o` and regex matching with `=~`. A fuller list of differences can be found in the [bash manual section on conditional constructs](http://www.gnu.org/software/bash/manual/bashref.html#Conditional-Constructs).
        > 
        > 
        > Use `[]` whenever you want your script to be portable across shells. Use `[[]]` if you want conditional expressions not supported by `[]` and don't need to be portable.
        > 
        > [Difference between single and double square brackets in Bash](https://stackoverflow.com/questions/13542832/difference-between-single-and-double-square-brackets-in-bash)
        > 

---

## 정리 전

### 뻘짓 (sed, awk)

[REAKWON :: [리눅스] sed 명령어를 이용해 원하는 정보를 추출 - 개념과 예제 모음 (tistory.com)](https://reakwon.tistory.com/164)

[Linux/기본명령어/sed - 인코덤, 생물정보 전문위키 (incodom.kr)](http://www.incodom.kr/Linux/%EA%B8%B0%EB%B3%B8%EB%AA%85%EB%A0%B9%EC%96%B4/sed)

[creating a blank line after some specific line using bash / linux - Stack Overflow](https://stackoverflow.com/questions/40553714/creating-a-blank-line-after-some-specific-line-using-bash-linux)

[[LINUX] 📚 awk 명령어 문법 마스터 💯 총정리 (tistory.com)](https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-awk-%EB%AA%85%EB%A0%B9%EC%96%B4-%EB%AC%B8%EB%B2%95-%EB%A7%88%EC%8A%A4%ED%84%B0-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC)

[이재원님의 이글루 (zum.com)](http://egloos.zum.com/slog2/v/3689816)

[[Linux] more, less, head, tail, 특정 라인 출력 sed, awk ④ (tistory.com)](https://it-serial.tistory.com/entry/Linux-%ED%8E%B8%EC%A7%91-%EA%B4%80%EB%A0%A8-%EB%AA%85%EB%A0%B9%EC%96%B4-2%ED%83%84-%ED%8A%B9%EC%A0%95-%EB%9D%BC%EC%9D%B8-%EC%B6%9C%EB%A0%A5-%E2%91%A3)

```bash
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print NR}'
1
2
3
4
5
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print 'hi''
awk: cmd. line:1: NR < 6 {print $0}; END {print hi
awk: cmd. line:1:                                 ^ unexpected newline or end of string
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print 'hi'}
> 
> d
> '
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms

codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print 'hi'}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms

codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print ''}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms
Network Engineering,Algorithms
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print '\n'}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms

codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print '\n'}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms

codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print '\n' > courses_test.csv}'
awk: cmd. line:1: NR < 6 {print $0}; END {print n > courses_test.csv}
awk: cmd. line:1:                                               ^ syntax error
codeally@e5272eaadc97:~/project$ cat courses_test.csv | awk -F, 'NR < 6 {print $0}; END {print '\n' > "courses_test.csv"}'
major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms
codeally@e5272eaadc97:~/project$
```

[[ORACLE,SQL] drop vs truncate vs Delete 차이점. 테이블 삭제, 데이터 삭제 명령어 알아보자. (tistory.com)](https://jhnyang.tistory.com/56)

### psql connect/disconnect

- psql connect
    
    ```bash
    psql --username=freecodecamp --dbname=postgres
    ```
    
- connect to certain database
    
    ```sql
    \c students
    ```
    
- database disconnect (back to bash)
    
    ```sql
    \q
    ```
    

- 파일을 저장하지 않고 Vim/Vi를 종료
    - Esc 키를 눌러 일반 모드로 전환하고 `:q!` 를 입력하고 Enter를 누른다

```bash
# psql에 `.sql`로 저장한 데이터베이스를 업로드

psql -U postgres < students.sql

# psql -U <dbname1> < <dbname2>.sql
```

- `\l` : list of databases
- `\d` : display tables and relations (in a database)
- `\d <table_name>` : details of the table
- bash에서 파일에 executable permission 부여:
    
    ```bash
    chmod +x 파일명.확장자
    ```
    
- echo -e
    - `echo` 명령어에서 `-e` 플래그를 사용하면 escape sequence를 사용할 수 있다
        - 예:
            
            ```bash
            codeally@970a460b6123:~/project$ echo -e 'hello\nworld'
            hello
            world
            ```
            

**SQL = Structured Query Language**

- language used to manage relational databases

- sh에서는
    - Place double quotes around it like this: `echo "$($PSQL "<query_here>")"`. This will make it so the output isn't all on one line.
    - 겹따옴표 사용
- sql에서는
    - Use the `=` to view all majors named Game Design. Don't forget that You need single quotes around text values.
    - 홑따옴표 사용

**SQL keywords**

- `WHERE`, `AND`, `OR`, `ORDER BY`, `LIMIT` 등…

- sql 쿼리에서 where 쓸 때 괄호를 쳐서 우선순위 설정 가능
    - 예: `SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' and (gpa > 3.8 or gpa < 2.0);`

- You can use `LIKE` to find patterns in text like this: `WHERE <column> LIKE '<pattern>'`.
- An underscore (`_`) in a pattern will return rows that have any character in that spot.
- Another pattern character is `%`. It means **anything** can be there. To find names that start with `W`, you could use `W%`. View the courses that end in `lgorithms`.
    - “anything”  = 모든 숫자, 글자, 공백, 기호 등등이 1개 이상 들어감
- Combine the two pattern matching characters to show courses that have a second letter of `e`.
    
    ```sql
    SELECT * FROM courses WHERE course LIKE '_e%';
    ```
    
- Try viewing the courses with a space in their names.
    - Use `LIKE` and a pattern with two `%` to view the courses with a space
    
    ```sql
    SELECT * FROM courses WHERE course LIKE '% %';
    ```
    
- You can use `NOT LIKE` to find things that don't match a pattern
- Try finding the ones that contain an `A`.
    
    ```sql
    SELECT * FROM courses WHERE course LIKE '%A%';
    ```
    
- `ILIKE` will ignore the case of the letters when matching
    - case-insensitive하게 제외하려면 `NOT ILIKE`
- All the fields that are empty or blank are `null`. You can access them using `IS NULL` as a condition like this: `WHERE <column> IS NULL`.
    - 반대는 `IS NOT NULL`.
- 정렬
    - `ORDER BY <column_name>`
    - at the end of a query
    - 기본값은 ascending (`ASC`) order.
    - 내림차순으로 하려면 쿼리 맨 끝에 `DESC` 넣기.
        - 예: `ORDER BY <column_name> DESC`
    - 정렬 기준 여러개 할 수도 있음. 쉼표로 구분
        - `ORDER BY <column_name1> DESC, <column_name2>`
- 리턴되는 행 수 지정: `LIMIT <number>`
    - 위에서부터 n개
- The order of the **keyword**s in your query matters. You cannot put `LIMIT` before `ORDER BY`, or either of them before `WHERE`.
    - `WHERE` → `ORDER BY` → `LIMIT` 순서.
    
    ```sql
    SELECT * FROM students WHERE gpa IS NOT NULL ORDER BY gpa DESC, first_name LIMIT 10;
    ```
    

## mathematic functions

- numerical columns에 사용 가능
- `MIN` : find minimum
    - `SELECT MIN(<column>) FROM <table>`
- 소수점 처리: `CEIL` & `FLOOR`
- `CEIL` : round a number **up to** the nearest whole number.
    - `CEIL(<number_to_round>)`
- 함수 겹쳐서 쓸 수 있음
    - `CEIL(AVG(<numerical_column>))`
- `ROUND` : round a number to the nearest whole number
    - 반올림할 소수점 자리 지정할 수 있음
    - `ROUND(<number_to_round>, <decimals_places>)`
        
        ```sql
        SELECT ROUND(AVG(major_id), 5) FROM students;
        ```
        
- `COUNT` : the number of entities in a table for the column
    - `COUNT(*)` 하면 모든 행을 셈.
    - `COUNT(<column>)` 하면 해당 열에서 데이터가 있는 행 (= not null인 entry)만 셈.
- `DISTINCT` : a function that will show you only unique values
    - `DISTINCT(<column>)`
- `GROUP BY` : ?
    - `SELECT <column> FROM <table> GROUP BY <column>`
    - `DISTINCT` 와 비슷하지만, 아무 aggregate functions (`MIN`, `MAX`, `COUNT`, 등등) 과 함께 쓸 수 있다.
        - 예: View the major_id column and number of students in each major_id.
            
            ```sql
            students=> SELECT major_id, COUNT(*) FROM students GROUP BY major_id;
            students=>           
            +----------+-------+
            | major_id | count |
            +----------+-------+
            |          |     8 |
            |       42 |     1 |
            |       41 |     6 |
            |       38 |     4 |
            |       36 |     6 |
            |       37 |     6 |
            +----------+-------+
            (6 rows)
            ```
            
    - When using `GROUP BY`, any columns in the `SELECT` area must be included in the `GROUP BY area`. Other columns must be used with any of the aggregate functions (`MAX`, `AVG`, `COUNT`, etc).
        - 예: View the unique major_id values with GROUP BY again, but see what the lowest GPA is in each of them.
            
            ```sql
            students=> SELECT major_id, MIN(gpa) FROM students GROUP BY major_id;
                     
            +----------+-----+
            | major_id | min |
            +----------+-----+
            |          | 2.3 |
            |       42 | 2.6 |
            |       41 | 2.1 |
            |       38 | 2.2 |
            |       36 | 1.9 |
            |       37 | 1.8 |
            +----------+-----+
            (6 rows)
            ```
            
    - `GROUP BY` 에는 `HAVING` 옵션이 있다.
        - `SELECT <column> FROM <table> GROUP BY <column> HAVING <condition>`
        - `HAVING` 뒤에 붙는 조건은 반드시 test가 포함된 aggregate function이어야 한다.
            - 예: `HAVING COUNT(*) > 0`
- `AS` : 출력결과에서 표시되는 열 이름 변경
    - `SELECT <column> AS <new_column_name>`
    - `SELECT <column1> AS <new_column_name1>, <column2>, <column3> AS <new_column_name3>`
    - 예:
        
        ```sql
        students=> SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;
        students=>               
        +----------+---------+-----+
        | major_id | min_gpa | max |
        +----------+---------+-----+
        |       41 |     2.1 | 4.0 |
        |       37 |     1.8 | 4.0 |
        +----------+---------+-----+
        (2 rows)
        ```
        

# JOIN

- 4 types: `FULL JOIN`, `INNER JOIN`, `LEFT JOIN`, `RIGHT JOIN`
    - 이 4개 기본형을 조합해서 다양한 형태의 `JOIN`을 만든다.
- `FULL JOIN`
    - `SELECT * FROM <table_1> FULL JOIN <table_2> ON <table_1>.<foreign_key_column> = <table_2>.<foreign_key_column>;`
        - `ON` 다음은 그냥 프리코드캠프 문제에서 나온 옵션—기본형은 아님
- A `LEFT JOIN` gets all rows from the left table, but only rows from the right table that are linked to from the left one.
- right, left의 기준은 철저히 코드이다—즉, 코드에서 먼저 입력한 테이블이 left, 나중에 입력한 테이블이 right이다 (영어는 왼쪽에서 오른쪽으로 읽으니까 코드를 눈으로 보면 left 테이블이 “말 그대로” 왼쪽에 적혀있게 된다)
- column 특정하기: `<table>.<column>`
    - 예: students 와 majors 두 테이블 합친 후 students 테이블의 major_id를 출력하기
        
        ```sql
        SELECT students.major_id FROM students FULL JOIN majors ON students.major_id = majors.major_id;
        ```
        
    - AS : rename 기능. 컬럼과 테이블 둘 다. 혹은 alias를 부여함.
        - `SELECT * FROM <table> AS <new_name>;`
        - 이렇게 해서 테이블명을 바꾸면, 이후에 해당 테이블을 언급(refer)할때는 새 alias를 사용하면 된다
            
            ```sql
            SELECT students.major_id FROM students FULL JOIN majors AS m ON students.major_id = m.major_id;
            SELECT s.major_id FROM students AS s FULL JOIN majors AS m ON s.major_id = m.major_id;
            ```
            
- `USING` : 단축키같은 역할을 하는 sql keyword. `JOIN` 할 때 foreign key가 두 테이블 모두에서  같은 열이름을 가지고 있으면 사용 가능.
    - `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>);`
        
        ```sql
        SELECT * FROM students FULL JOIN majors USING(major_id);
        ```
        

## 3개 이상의 테이블 합치기

- `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>) FULL JOIN <table_3> USING(<column>)`
    - 이렇게 하면 순차적으로 테이블 1과 2를 합치고, 합쳐진 테이블을 left table로 삼아서 테이블 3과 합친다.
        
        ```sql
        SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id);
        ```
        

![SQL_Joins.svg](SQL%20Basics%20f5cba427fbcb41619647a2c89ac88512/SQL_Joins.svg)

![joins-in-mysql-1.png](SQL%20Basics%20f5cba427fbcb41619647a2c89ac88512/joins-in-mysql-1.png)

---

