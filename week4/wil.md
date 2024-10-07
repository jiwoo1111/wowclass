# 3주차(10월1일)

# 데이터 베이스

- RDBMS
    - 관계형 데이터 베이스
    - 테이블에 데이터를 저장
    - 가로: row
    - 세로: 컬럼
- RDBMS를 사용하는 이유
    - 데이터 구조화
    - 중복 데이터 최소화
- in Django
    - models.py가 알아서 해줌
    - 관계형 DB의 특성만 알아두면 됨
- Primary key
    - 고유한 값
    - 잘 변경되지 않는 값
    - 모든 로우가 가지는 값(NOT NULL)
    - 모든 테이블에는 반드시 PK가 필요
    - 적당한 PK가 없을 경우 새로운 엔터티를 생성 (ex 주문번호)
- 정규화
    - 주문 테이블, 유저 테이블 연동하기
    - 테이블 쪼개기
    - 주문 테이블 내 유저id 엔터티 : 외래키 (FK)
- 장고의 DBMS
    - DB 생성
    - 데이터 입출력, 양식 변환
    - DBMS에 비종속
- 클래스
    - 과자 틀
    - 객체: 틀을 통해 만들어진 과자
    
    ```python
    """ models.py """
    from django.db import models
    
    class Student(models.Model):
    	id = models.CharField(max_Length=7)
    	name = models.CharField(max_Length=20)
    	address = models.TextField()
    	birth_date = models.DateField()
    ```
    
    - views 에선 model Class를 이용해 DB 접근