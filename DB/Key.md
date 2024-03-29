# Key

- [Key](#key)
    - [Key란? 검색이나 정렬 시 Tuple을 구분할 수 있는 기준이 되는 Attribute.](#key란-검색이나-정렬-시-tuple을-구분할-수-있는-기준이-되는-attribute)
  - [1. Candidate Key(후보키)](#1-candidate-key후보키)
  - [2. Primary Key(기본키)](#2-primary-key기본키)
  - [3. Alternate Key(대체키)](#3-alternate-key대체키)
  - [4. Super Key(슈퍼키)](#4-super-key슈퍼키)
  - [5. Foreignn Key(외래키)](#5-foreignn-key외래키)
    - [Null 값?](#null-값)
  - [참고](#참고)


### Key란? 검색이나 정렬 시 Tuple을 구분할 수 있는 기준이 되는 Attribute.

  
![](https://user-images.githubusercontent.com/33534771/75773133-a4d02680-5d90-11ea-8ad0-ac4b85e438d2.png)

## 1. Candidate Key(후보키)

- 릴레이션을 구성하는 속성들 중에서 Tuple을 유일하게 식별할 수 있는 속성들의 부분 집합을 의미한다.(기본키로 사용할 수 있는 속성들을 후보키라 한다.)

- 모든 릴레이션은 반드시 하나 이상의 후보 키를 가져야 한다.

- 릴레이션에 있는 모든 튜플에 대해서 유일성과 최소성을 만족시켜야 한다.

아래 2가지 조건을 만족해야 한다.

 1. 유일성 : Key로 하나의 Tuple을 유일하게 식별할 수 있음.

2. 최소성 : 꼭 필요한 속성으로만 구성.

Ex) [학생] 릴레이션에서 학번이나 주민번호는 다른 레코드를 유일하게 구별할 수 있는 기본키로 사용할 수 있으므로 후보키가 될 수 있다. 즉, 기본키가 될 수 있는 키들을 후보키라 한다.

  

## 2. Primary Key(기본키)

- 후보 키 중 선택한 Main key

- 한 릴레이션에서 특정 튜플을 유일하게 구별할 수 있는 속성

- Null 값을 가질 수 없다.(개체 무결성의 첫 번째 조건)

- 기본 키로 정의된 속성에는 동일한 값이 중복되어 저장될 수 없다.(개체 무결성의 두 번째 조건)

아래 조건을 만족해야 한다.

1. 유일성 : 기본키를 구성하는 컬럼은 테이블에서 레코드를 식별할 수 있도록 유일해야 한다.

2. 최소성 : 유일성을 만족하는 한도 내에서 최소한의 컬럼(하나 이상)으로 구성되어야 한다.

3. 개체 무결성 : 기본키가 가지고 있는 값의 유일성을 보장받아야 한다.

Ex)
[학생] 릴레이션에는 학번이나 주민 번호가 기본키가 될 수 있고, [수강] 릴레이션에는 학번+과목명으로 조합해야 기본키가 만들어질 수 있다. 왜냐하면 [수강] 릴레이션에서는 학번 속성과 과목명 속성은 개별적으로 기본키로 사용할 수 없다. 다른 튜플들과 구별되지 않기 때문이다.

  

## 3. Alternate Key(대체키)

- 후보키가 둘 이상일 때, 기본 키를 제외한 나머지 후보키들을 말한다.

- 보조키라고도 한다.

Ex)
[학생] 릴레이션에서 학번을 기본키로 정하면 주민번호 는 대체키가 된다.

  

## 4. Super Key(슈퍼키)

- 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키로서 릴레이션을 구성하는 모든 튜플 중 슈퍼키로 구성된 속성의 집합과 동일한 값을 나타내지 않는다.

- 릴레이션을 구성하는 모든 튜플에 대해서 유일성은 만족하지만, 최소성은 만족시키지 못한다.

Ex)
[학생] 릴레이션에서는 학번, 주민번호, 학번+주민번호, 학번+주민번호+성명 등으로 슈퍼키를 구성할 수 있다. 또한, 여기서 최소성을 만족시키지 못한다는 말은 학번+주민번호+성명이 슈퍼키인 경우, 3개의 속성 조합을 통해 다른 튜플과 구별이 가능하지만, 성명 단독적으로 슈퍼키를 사용했을 때는 구별이 가능하지 않기 때문에 최소성을 만족시키지 못한다.

  

즉, 뭉쳤을 경우 유일성이 생기고 흩어지면 몇몇 속성들은 독단적으로 유일성이 있는 키로 사용할 수 없다. 이것을 최소성을 만족하지 못한다고 한다.

  

## 5. Foreignn Key(외래키)

- 관계(Relation)를 맺고 있는 릴레이션 R1,R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성을 외래키라고 한다.

- 외래키는 참조되는 릴레이션의 기본키와 대응되어 릴레이션 간에 참조 관계를 표현하는 데 중요한 도구로 사용된다.

- 외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없다.(참조 무결성의 조건)

Ex)
[수강] 릴레이션이 [학생] 릴레이션을 참조하고 있으므로, [학생] 릴레이션의 학번은 기본키이고, [수강] 릴레이션의 학번은 외래키이다.

- 즉, 각 릴레이션의 입장에서 속성은 기본키가 되기도 하고, 외래키가 되기도 한다.
-> [수강] 릴레이션의 학번에는 [학생] 릴레이션의 학번에 없는 값은 입력할 수 없다.


### Null 값?
데이터베이스에서 아직 알려지지 않았거나, 모르는 값으로서 "해당 없음" 등의 이유로 정보 부재를 나타내기 위해 사용하는, 이론적으로 아무것도 없는 특수한 데이터를 뜻한다.

  

## 참고

[DataBase] 키(Key)의 개념 및 종류

  

https://github.com/WooVictory/Ready-For-Tech-Interview/blob/master/Database/Key(%ED%82%A4).md