# 5주차(10월 8일)

# Model & ORM

- 하나의 프로젝트는 여러 개의 어플리케이션으로 구성
- 프로젝트
    - 개발자가 장고로 만드는 소프트웨어 전체
- 어플리케이션
    - 프로젝트 내에서 기능별로 쪼개놓은 단위
- 프로젝트 구조



- DB와 Model



- Model의 역할
    - [Models.py](http://Models.py)에 클래스 생성시 장고가 클래스를 토대로 DB 테이블 생성
    - DB 테이블에서 값을 조회 시 models.py에 만들어놓은 클래스의 객체에 값을 담아 반환

# SQL & ORM

```sql
INSERT INTO 학회원 (학번, 이름, 주소) value (C011057, 김지우, 서울시 마포구)
SELECT (학번, 이름, 주소) 
FROM 학회원
WHERE 주소 = 서울시 마포구
```

- 장고 ORM 사용법
    - 클래스이름.objects를 이용해 DB에 저장된 값에 접근
    - 클래스이름.objects.all() 함수
        - 모든 테이블 정보를 객체로 만들어 리스트에 넣어 반환
    - 클래스이름.objects.get() 함수
        - 조건에 맞는 데이터를 객체로 만들어 반환
        
        ```python
        Student.objects.get('id='C011057')
        ```
        
    - 클래스이름.objects.filter() 함수
        - 조건에 맞는 정보들을 객체로 만들어 리스트에 넣어 반환
- 동적 html 생성
    
    ```python
    def index(request):
    		name = 'kim'
    		context = {'name':name}
    		return render(request, 'index.html',contex)
    ```
    
    - render 함수 html 파일 경로 뒤에는 html 내에 넣고 싶은 정보를 dictionary에 담아 넘김
    - render 함수 앞의 request: 장고에서 만들어서 넣어준 HTTP Request 객체
    - render 함수 두 번째 인자는 응답할 html 파일 이름
    - render 함수 세 번째 인자는 html 파일에서 사용할 dictionary
    
    ```html
    <h1>안녕하세요</h1>
    <p>{{name}}씨 반갑습니다</p>
    ```
    
- 웹 통신 흐름
    

    
- HTML
    - 사용자가 보는 웹페이지 구조화
    - 브라우저가 파일 읽고 난 뒤 페이지 렌더링
    - 태그를 이용해 내용을 꾸미거나 기능 추가
- CSS
    - 웹 페이지 꾸미기용
    - HTML 요소에 선택적으로 스타일 적용
- HTML 태그
    - h1, h2, h3
        - 제목 생성 태그
        - 숫자가 낮아질 수록 폰트 크기 감소
    - p
        - 하이퍼링크 참조
        
        ```html
        <a href='www.google.com'>google</a>
        ```
        
    - ul,ol,li
        - 목록(list)를 만들어주는 태그, ul, ol 태그 안에 li 태그 삽입
        - ul : 순서가 없는 목록(unordered list)
        - ol : 순서가 있는 목록(ordered list)
        
        ```html
        <ul>
        	<li>이혁</li>
        	<li>김성훈</li>
        	<li>홍길동</li>
        </ul>
        
        <ol>
        	<li>이혁</li>
        	<li>김성훈</li>
        	<li>홍길동</li>
        </ol>
        ```
        
    - 이혁
    - 김성훈
    - 홍길동
    1. 이혁
    2. 김성훈
    3. 홍길동
    
    - div
        - 특별한 기능 x, 레이아웃을 나누기 위해 사용
        
        ```html
        <div style="background-color:red">content1</div>
        <div style="background-color:blue">content2</div>
        ```
        
    - form, input
        - 데이터를 입력받고 전송하기 위한 태그
        - input 태그로 데이터 입력, form 태그의 action 속성 → url 전송
        
        ```html
        <form action="localhost:8000/create">
        	<input type="text"/>
        	<input type="submit"/>
        </form>
        ```
        

# 장고 템플릿

- 장고는 HTML을 동적으로 생성
- 태그 생성은 불가, 태그 내 내용을 동적으로 변경은 가능
- 사용법
    - render 함수 마지막 인자에 원하는 데이터를 담은 dictionary 삽입
    - dictionary 의 key 값은 문자열
    - {{}} : 중괄호 2개 안에 key값을 넣어 사용
- 장고 ORM 사용법
    - 클래스이름.objects.get() 이라는 함수 → 조건에 맞는 데이터를 객체로 만들어 반환
    - 객체 내부 데이터 접근시, ‘객체이름.객체변수이름’ 으로 사용