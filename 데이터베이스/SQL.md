# SQL


> DDL 데이터 정의어
* create
* alter 
* drop
* truncate

> DML

* insert
* select
* update 
* delete

>DCL
* grant
* revoke
* commit
* rollback


> SHOW
 * show database
 * show tables
 * show table satatus

 번외 use [데이타베이스 이름]
 
> 관계 연산자 
* OR
* AND
* 조건 연산자 (=,<,>,>=,<=,!=)
* 관계  연산자 (NOT, AND,OR)
* between 

쓰는 이유 : 연산자의 조합으로 데이터를 효율적으로 추출


> LIKE 연산자

**문자열의 내용 검색하기 위해 like 연산자 사용 
한 글자와 매치하기 위해서 '_' 사용**

`ex) select * from city where CountryCode like 'KO_';`


% :  문자 뒤에 % 무엇이든 허용

`ex) select * from city where CountryCode like 'Tel %';`

___

>sub query

**쿼리문 안에 또 쿼리문이 들어 있는 것 서브 쿼리의 결과가 둘 이상이 되면 에러 발생**

`ex) select * from city where CountryCode = (select CountryCode from city where name = 'Seoul');` 

>any

**서브쿼리의 여러 개의 결과 중 한 가지만 만족해도 가능
some은 any와 동일한 의미로 사용 =any 구문은 in과 동일한 의미**

`ex) select * from city where Population > any (select Population from city where District = 'New York');`

>all 

**서브쿼리의 여러 개의 결과를 모두 만족 시켜야함**

`ex) select * from city where Population > ALL (select Population from city where District = 'New York');` 


>order by

**결과가 출력되는 순서를 조절하는 구문**

내림차순 desc

오름차순 asc

defualte asc 

`ex) select * from city order by Population desc, CountryCode asc; (두개로도 가능)`

distinct : 중복 제거
중복된 것은 1개씩 보여주면서 출력
테이블의 크기가 클수록 효율적

select distinct CountryCode from city;

limit : 출력 개수를 제한
서버 처리량을 많이 사용해 서버의 전반적인 성능을 나쁘게 하는 아성 쿼리문을 
개선할 때 사용 

select * from city order by Population desc limit 10;

group by : 그룹으로 묶어주는 역할


집계함수 사용
avg(): 평균
min(): 최소값
max(): 최대값
count(): 행의 개수
count(distinct): 중복 제외된 행의 개수 
stdev(): 표준 편차 
variance(): 분산 
효율적인 데이터 그룹화 
읽기 좋게 하기 위해 별칭 사용

select CountryCode, max(Population) from city group by CountryCode;


having : where와 비슷한 개념으로 조건 제한 
having절은 반드시 group by 절 다음에 나와야 함 

select CountryCode, max(Population) from city group by CountryCode having max(Population) > 8000000;

rollup : 총합 또는 중간 합계가 필요할 경우 사용
group by 절과 함께 with rollup문 사용


join : 데이터베이스 내의 여러 테이블에서 가져온 레코드를 조합하여 하나의 테이블이나
결과 집합으로 표현 

select * from city join country on city.CountryCode = country.Code;

mysql 내장함수 
사용자의 편의를 위해 다양한 기능의 내장 함수를 미리 정의하여 제공
대표적인 내장함수의 종류
문자열 함수
수학 함수 
날짜와 시간 함수 

length() : 전달받은 문자열의 길이를 반환
concat() : 전달받은 문자열을 모두 결합하여 하나의 문자열로 반환 
locate() : 문자열 내에서 찾는 문자열이 처음으로 나타나는 위치를 찾아서 해당 위치를 반환 
mySQL에서는 문자열의 시작 인덱스를 1부터 계산 

left() : 문자열의 왼쪽부터 지정한 개수만큼의 문자를 반환 
right() : 문자열의 오른쪽부터 지정한 개수만큼의 문자를 반환 

lower() : 문자열의 문자를 모두 소문자로 변경
upper() : 문자열의 문자를 모두 대문자로 변경 

replace() : 문자열에서 특정 문자열을 대체 문자로 교체 

trim() : 문자열의 앞이나 뒤, 또는 양쪽 모두에 있는 특정 문자를 제거

format() : 숫자타입의 데이터를 세자리마다 쉼표를 사용하는 '#,###,###,##' 형식으로 변환

floor() : 내림
ceil() : 올림
round() : 반올림

sort() : 양의 제곱근 
pow() : 첫번째 인수로는 밑수를 전달하고, 두번째 인수로는 지수를 전달하여 거듭제곱 계산
exp() : 인수로 지수를 전달 받아, e의 거듭제곱을 계산
log() : 자연로그 값을 계산 

sin() : 사인값 반환 
cos() : 코사인값 반환 
tan() : 탄젠트값 반환 

abs() : 절대값을 반환 
rand() : 0.0보다 크거나 같고 1.0보다 작은 하나의 실수를 무작위로 생성

날짜함수 
now() : 현재 날짜와 시간을 반환 
curdate() : 현재 날짜를 반환
curtime(): 현재 시각을 반환 

date() : 전달 받은 값에 해당 하는 날짜 정보를 반환 
month() : 월에 해당하는 값을 반환 
day() : 일에 해당하는 값을 반환 
hour() : 시간에 해당하는 값을 반환 
minute() : 분에 해당하는 값을 반환 
second() : 초에 해당하는 값을 반환 
monthname() : 월에 해당하는 이름을 반환 
dayname() : 요일에 해당하는 이름을 반환 


테이블 만들기 
create table as select : 똑같은 테이블을 만들 수 있음 
create table city2 as select * from city; (city 테이블과 똑같은 city2 테이블 생성)

데이터 베이스 만들기 
create database test;


테이블 생성 
create table test (
 id int not null primary key
 name varchar(40) null,
 gender varchar(10) nul;
);


테이블 컬럼 추가
alter table test add col4 varchar(40) null;

테이블 컬럼 변경 
alter table test modify col4 int null;

테이블 컬럼 삭제 
alter table test drop col4;

index : 인덱스
테이블에서 원하는 데이터를 빠르게 찾기 위해 사용 
일반적으로 데이터를 검색할 때 순서대로 테이블 전체를 검색하므로 데이터가 많으면 
많을수록 탐색하는 시간이 늘어남 

검색과 질의를 할 때 테이블 전체를 읽지 않기 때문에 빠름
설정된 컬럼 값을 포함한 데이터의 삽입, 삭제, 수정 작업이 원본 테이블에서 이루어질 경우, 인덱스도 함께 수정되어야함

인덱스가 있는 테이블은 처리 속도가 느려질 수 있으므로 수정보다는 검색이 자주 사용되는 테이블에서 사용하는 것이 좋음 

create index 문을 사용하여 인덱스를 생성 

create index col1index
on test (col1)

인덱스 보고 싶을 때 
show index from test;  

create unique index 중복 값을 허용하지 않는 인덱스

create index col2index on test (col2);

인덱스 삭제 

alter table test drop index col2index;

view  : 가상 테이블 
실제 테이블처럼 행과 열을 가지고 있지만, 실제로 데이터를 저장하진 않음

뷰를 사용하면 여러 테이블이나 뷰를 하나의 테이블처럼 볼 수 있음 

뷰 장점: 특정 사용자에게 테이블 전체가 아닌 필요한 컬럼만 보여줄 수 있음
복잡한 쿼리를 단순화해서 사용 
쿼리 재사용 사능

뷰의 단점 :
한번 정의된 뷰는 변경할 수 없음 
삽입, 삭제, 갱신 작업에 많은 제한 사항을 가짐
자신만의 인덱스를 가질 수 없음 

뷰 생성 
create view testView as select col1, col2 from test;

뷰 보기
select * from testView;


insert : 값 넣기 

insert into test values('123',111,111);

update : 기존 입력되어 있는 값 변경하는 구문 
where절 생략 가능하나 테이블의 전체 행의 내용 변경 

update test set col1=1, col2=2, col3='test' where id =1;

delete : 데이터 삭제 
복구 가능 
delete from test where id = 1;

truncate table test; 데이트 다 삭제 복구 불가


dorp table test;

커밋이 안됌 ;;;