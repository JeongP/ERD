# ERD

## 전체흐름

1. 업무파악
2. 개념적 데이터 모델링 (E-R diagram) -> 개념들은 어디에 어떻게 상호작용하고 있는지.
3. 논리적 데이터 모델링 -> 관계형 DB에 맞게 표로 정리
4. 물리적 데이터 모델링 -> DB 제품 선택 및 실제 테이블 작성.(sql 코드를 갖게됨)


## 개념적 데이터 모델링

>세상의 개념을 정보(속성-attribute), 그룹(개체-entity), 관계(relation)로 어떻게 이루어져 있는지 나타내는 것. (ER diagram)     

* entity => table
* attribute => column
* relation => pk, fk
 
      
### 식별자
    
* 후보키
  * 테이블 내에서 모든 행을 유일하게 구분할 수 있는 컬럼들의 후보.   

* 기본키(pk)
  * 후보키 중 하나.
  * 중복 데이터 삽입 방지, 하나의 테이블에서 고유한 행을 선택할 수 있게함.
  * 개체 무결성 보장.
    
* 대체키 
  * 후보키 - 기본키.
    
* 중복키
  * 두개 이상의 속성을 합쳐서 식별자로 갖는것
    
* 외래키
  * 다른 테이블의 행을 식별할 수 있는 키
  * 참조 무결성 보장.
  
    
### 관계
* entity 간의 연결 관계.
* pk와 fk로 서로간의 관계를 맺을 수 있음.
* cardinality
* optionality: 있을수도 있고 없을수도 있고
* mandatory: 필수 관계를 나타냄.
    

## 논리적 데이터 모델링
* ER-diagram을 RDB 스럽게 변환하는 과정
    
    
### 관계의 종류
http://bit.ly/2wV2SFj
* 1:1
* 1:N
* M:N
    
### 정규화
    

#### 1NF (Atomic columns)
* 각 column의 값이 Atomic 해야한다.
  * atomic하지 않다면 조회,join 등의 작업에서 문제 발생할 수 있음.
  * ex) select * from topic where tag = 'free'
 

#### 2NF (No Partial dependencies)
* 부분 종속성이 없어야 한다. 
  * 부분 종속을 가지고 있다면, 중복 데이터 생길 가능성 있음.

#### 3NF (No transitive dependencies)
* 이행적 종속성이 없어야 한다.
  * 이 또한, 중복 데이터를 만들어 버릴 수 있음.


## DB의 성능을 향상시키기 위해서는...
* index를 통한 접근 속도 향상. (read 이점, write 손해)
* cache를 통한 db 부하 줄여서 성능 향상.
* 이로 안된다면 구조 자체를 수정.

### 역정규화
http://bit.ly/2WLMCko
* 역정규화는 중복이나 이런것들에서 손해를 보지만 read하는데 있어서 이점을 취할 수 있음.
(join과 같은 비싼 연산을 하지 않고 원하는 데이터를 끌어올 수 있기 때문에)
