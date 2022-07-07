
# HTML 정리


### 기본 구조
    !DOCTYPE html :웹 문서의 유형을 html로 지정 
    html lang="ko"	문서를 html로 시작, 언어를 한국어로 지정
    head	주로 브라우저의 정보를 입력하는 곳
    meta	메타 데이터 입력, (주로 meta charset="UTF-8" 처럼입력)
    title	문서 제목
    body	문서 내용을 입력

example code

    <!DOCTYPE html>
    <html lang="ko">
    <head>
        <meta charset="UTF-8">
        <title>Document</title>
    </head>
    <body>
        body...
    </body>
    </html>

### Body Tag
#### Text 입력
    h1, ..., h6	제목
    p               단락
    br	        줄 바꿈, 닫기태그 없음
    blockquote	인용문, 들여쓰기 적용됨
    strong	        텍스트 굵게, 주로 중요한 내용일 때
    b	        텍스트 굵게, 단순히 굵게 표시할 때
    em	        텍스트 기울임, emphasis의 준말, 강조할 때
    i	        텍스트 기울임, italic의 준말, 단순히 기울여 표시할 때
    u	        텍스트 밑줄
    s	        텍스트 취소선

#### 목록 입력
 _ol: ordered list (순서 있는 목록)_
   > type:
   > "1"	숫자(기본값)
   > "a"	영문 소문자
   > "A"	영문 대문자
   > "i"	로마 숫자 소문자
   > "I"	로마 숫자 대문자

 _ul: unordered list (순서 없는 목록)_

#### 표(Table) 입력
    Tag:
        <table>         표 만들기
    
    Attributes:
        <caption>	    표 제목
        <tr>	    행 삽입
        <td>	    셀 삽입
        <th>	    셀 삽입(진하게 표시)
        <thead>	    표 중 제목, 여러 페이지에 걸쳐 고정 가능
        <tbody>	    표 중 본문
        <tfoot>	    표 중 요약, 여러 페이지에 걸쳐 고정 가능

__Example__

    <table>
    <tr>
        <td>1행 1열</td>
        <td>1행 2열</td>
    </tr>
    <tr>
        <td>2행 1열</td>
        <td>2행 2열</td>
    </tr>
    </table>

__행/열 합치기__

    rowspan="2":	2개의 행 합치기
    colspan="2":	2개의 열 합치기

#### 이미지 입력
    Tag:
        <img>	    이미지 삽입
    
    Attributes:
        src=	    이미지 파일 경로
        alt=	    대체용 텍스트
        width&height    가로, 세로 크기 조절
        %	            브라우저 창의 크기 단위
        px	            픽셀 단위

#### 하이퍼 링크
    Tag:
        <a>	                하이퍼 링크 

    Attributes:
        href=	        링크 주소
        target="_blank"	새 탭에서 열기

__Example__

    <a href="링크할 주소">텍스트 또는 이미지</a> 
=> <a href="#">텍스트 또는 이미지</a>

    <p><a href="~">표시 텍스트</a></p>
=> <p><a href="#">표시 텍스트</a></p>

    <a><img src="이미지 파일 경로" alt></a>
=> <a href="#"><img src=""></a>

#### 폼(Form) 입력

    <form>	        폼 만들기
    Tag:
    <fieldset>	폼 내부에서 구역을 나눔
    <legend>	구역 제목 붙이기

    Attributes:
    method
        -> get	사용자 입력 내용이 드러나게 서버로 넘겨줌
        -> post	사용자 입력 내용이 드러나지 않게 서버로 넘겨줌
    name	        자바스크립트로 폼 이름 지정
    action      	서버 프로그램 지정
    target      	열어볼 파일 위치 지정
    autocomplete	자동 완성 기능 지정(기본값 on)
        
레이블(Label)

    [기본형] 
    <label>레이블명<input></label>
-> <label>레이블명<input></label>

    [Label + Form]
    <label for="id명">레이블명<input id="id명"></label>
-> <label for="id명">레이블명<input id="id명"></label>


#### Input

    Attributes: type=
    
    values:
    text	        한 줄 텍스트
    password	비밀번호
     -> Sub-attributes:
        size=	    화면에 출력할 글자 수
        value=	    text 필드에 보여줄 내용, password에서 사용 안함
        maxlength=	    최대 입력 가능한 글자 수
    
    search	        검색
    url	        url
    email	        이메일 주소
    tel	        전화번호

    checkbox	체크박스 (중복 체크)
    radio	        라디오 버튼 (unique 체크)
    -> Sub-attributes:
        value=	    서버에 전달될 값
        checked=	    기본으로 선택하고 싶은 항목
        name=	    radio 전용, 여러 옵션의 공통 이름

    number	        숫자 스핀 박스(버튼으로 숫자 조절)
    range	        숫자 슬라이드 막대
    -> Sub-attributes:  
            min=	최소값(기본값 0)
            max=	최대값(기본값 100)
            step=	조정할 단위값(기본값 1)
            value=	초기값

    date	        local - 연, 월, 일
    month	        local - 연, 월
    week	        local - 연, 주
    time	        local - 시, 분, 초, 분할 초
    datetime	UTC - 연, 월, 일, 시, 분, 초, 분할 초
    datetime-local	local - 연, 월, 일, 시, 분, 초, 분할 초

    submit	        전송 버튼
    reset	        리셋 버튼
    -> Sub-attributes:  
            value=	버튼에 표시할 내용

    image	        submit 버튼 이미지
    -> Sub-attributes:  
            src=	이미지 경로
            alt=	대체 텍스트 (load fail시 대체되는 text)

    button	        일반 버튼
    -> Sub-attributes:  
            value=	        버튼에 표시할 내용
            onclick=	클릭 시 실행할 JS함수

    file	        파일 첨부 버튼
    hidden	        사용자에게 보이지 않는 값 필드

__Input의 다른 attributes__

    autofocus=	페이지를 불러오자마자 마우스 포인터가 표시

    placeholder=	(input박스에)힌트를 표시, 내용을 입력하면 사라짐
    예) 아이디를 입력하세요.

    readonly=	읽기 전용
    예) readonly="readonly"

    readonly=       "true"

    required=	필수 입력 필드
    예) required="required"

__Input 의 다른 Tags__

    <textarea>	여러 줄의 텍스트 입력 영역
        rows=	세로 줄 수, 길 경우 스크롤 막대가 생성됨
        cols=	가로 너비(문자 단위)
    
    <select>	드롭다운 목록 생성
        size=	항목 개수
        multiple=	둘 이상의 항목을 선택
        <option>
            value=	    서버에 전달될 값
            selected=   기본 선택 항목
    <datalist>	미리 입력된 데이터 목록
    <option>	value=	서버에 전달될 값
    <button>	버튼
        type="submit"	폼을 서버로 전송
        type="reset"	폼 초기화
        type="button"	일반 버튼, <input type="button">과 같음