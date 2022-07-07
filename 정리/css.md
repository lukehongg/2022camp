# CSS 정리

### CSS + HTML 연결
    <HTML>
    <link rel="stylesheet" href="css파일경로">


### 선택자

__기본 선택자__

    * { }	        전체 요소
    p { }	        p 태그        
    .exclass { }	exclass라는 class를 사용하는 태그
    #exid { }	exid라는 id를 사용하는 태그 (한번만 적용 가능)

__고급 선택자__

    section p { }	    section 요소의 모든 p 요소 선택 (자식의 자식까지 적용)
    section > p { }	    section 요소의 바로 아래 p 요소 선택
    h1 + p { }	    h1 요소의 바로 다음 형제 p요소 선택
    h1 ~ p { }	    h1 요소의 모든 형제 p 요소 선택
    [class ~= button]   class 요소 중에서 button 속성값을 포함하는 요소 선택

    a[href]	            a 요소 중에서 href 속성이 있는 요소 선택
    a[target = _blank]  a 요소 중에서 target속성값이 _blank인 요소 선택
    a[title |= us]	    a 요소 중에서 "us" 또는 "us-"로 시작하는 요소 선택
    a[title ^= eng]	    a 요소 중에서 eng로 시작하는 요소 선택
    [href $= xls]	    href 속성값이 xls로 끝나는 요소 선택
    [href *= w3]	    href 속성값이 w3를 포함하는 요소 선택

### Font

    font-family     글꼴지정
    font-size       글자 크기 지정
                        em	        부모 요소 대문자 M의 너비 기준
                        rem	        root에서 지정한 크기 기준
                        ex	        소문자 x의 높이
                        px	        픽셀 단위
                        pt	        포인트 단위

    font-style      글꼴 스타일 지정
                        normal	일반
                        italic	이탤릭체
                        oblique	일반 글꼴을 기울임

    font-weight     글자 굵기 지정
                        normal	보통
                        bold	굵게
                        bolder	원래보다 더 굵게
                        lighter	원래보다 더 가늘게

### Text

    color           글자 색 조절
    text-align      텍스트 정렬
                        left, right, center,
                         justify, match-parent...

    line-height     줄 간격 조절, 상중하 조절 (중앙: height와 맞추기)

    text-decoration 줄 표시
                        underline, overline, line-through(취소선)

    text-shadow     그림자 효과 (가로, 세로, 번짐정도, 색상 순)
                        양수: 오른쪽/아래, 범짐
                        음수: 왼족/위, 뭉치기
    text-transform  대소 문자 변환
                        capitalize(첫 글자), uppercase, lowercase..

### 목록

    list-style-type:
        disc	                ●
        circle	                ○
        square	                ■
        decimal	                1, 2, 3, ...
        decimal-leading-zero	01, 02, 03, ...
        lower-roman	                i, ii, iii, ...
        upper-roman	                I, II, III, ...
        lower-alpha	                a, b, c, ...
        upper-alpha                 A, B, C, ...
        none

    list-style-image:   불릿 대시 이미지 사용
    ex) ul { list-style-image: url('PATH') }

### 표 (caption)

    caption-side (표 제목)
        top, bottom

    border (굵기 + 스타일 + 색상)
        ex) 1px solid blue
    
    border-collapse(border로 인한 중복되는 줄 정리)
        collapse: 합치기
        separate: 따로 표시 (Default)

### BOX

    콘텐츠 영역:
        width, height       콘텐츠 영역의 크기를 정함
                            px, em, %, auto
    
    박스 전체:
        box-sizing          box-sizing: border-box
                border-box      테두리 포함
                content-box     Default

    box-shadow              박스에 그림자 효과

    overflow                박스보다 큰 content 정리
                visible	내용이 넘쳐도 다 표시
                hidden	넘치는 부분 숨기기
                scroll	가로/세로 스크롤 바 생성
                auto	세로 스크롤 바 생성


### Border
참조: [border](https://www.w3schools.com/css/css_border.asp)

    border-style
    
    border-width        테두리 두께 (top, right,bottom, left 순서)
                        thin, medium, thick
    border-color
    border-radius       둥근 테두리
                        px, em, % 
    
### 여백

__margin__ : 요소 간 여백

        요소를 중앙에 위치: 
        #container{
            margin-left: auto;
            margin-right: auto;
        }
        #container {
            margin: 20px auto;
        }

__padding__: 테두리와 콘텐츠 사이

### float

    float       left, right, none

    clear       float 해제 
    (float가 적용된 요소의 다음 요소도 floatrk 적용됨 -> 이를 해제)
                left, right, both (left, right, 둘다 해제)

### Position
    static	        문서흐름에 맞춰 배치(기본값)
    relative	문서흐름 + 위치지정
    absolute	기준 : relative값을 사용한 상위요소
    fixed	        기준 : 브라우저 창
    sticky          고정된 위치에서 스크롤의 영향을 받지 않는요소
    -> top value 줘야함 (top: 0) + height 값이 정해져있어야함

### background

__그라데이션__

    linear-gradient: (중앙기준 방햑/각도, 색상 From, to)
    ex) linear-gradient: to right bottom, blue, white;

    color-stop(색상중앙지점 설정)
    ex) background: linear-gradient(to bottom, #06f, white 30%, #06f);

    (원형 그라데이션)
    radial-gradient(모양, 크기 at 위치, 색상중지점);
    ex) background: radial-gradient(circle, white, yellow, red); 
    -> (Default모양: 타원형)

    ex2) background: radial-gradient(circle at 20% 20%, white, blue);
    -> (at 위치) 20% 20%에서 시작하여 흰색에서 파란색으로 바뀌는 원형 그러데이션 

### 가상 Class

__사용자 반응에 따른 가상 클래스__

    :link	                방문하지 않은 링크
    :visited	        방문한 링크
    :hover	                마우스 포인터가 올려진 요소
    :active	                활성화된 요소(웹 링크, 이미지 등)
    :focus	                마우스 포인터, 커서가 맞춰진 요소

__요소 상태에 따른 가상 클래스__

    :target	                앵커(한 문서안의 다른 위치)
    ※ 다른 페이지로 이동할 땐 링크를 이용
    :enabled, :disabled	사용 가능, 불가능한 요소
    :checked	        선택한 요소(라디오 박스, 체크 박스 등)
    :not	                특정 요소를 제외한 요소

__구조에 따른 가상 클래스__
    
    :first-child	        첫번째 자식
    :last-child	        마지막 자식
    :nth-child(n)	        n번째 자식
    :nth-last-child(n)	끝에서 n번째 자식
    :only-child	        유일한 자식
    A:first-of-type	        자식 A 중 첫번째
    A:last-of-type	        자식 A 중 마지막
    A:nth-of-type(n)	자식 A 중 n번째
    A:nth-last-of-type(n)	자식 A 중 끝에서 n번째
    A:only-of-type	        유일한 자식 A


### Transform

    translate(tx, ty)   x축, y축으로 이동
    translateX(tx)	    x축으로 이동
    translateY(ty)	    y축으로 이동
    scale(sx, sy)	    x축, y축으로 확대 · 축소
    scaleX(sx)	    x축으로 sx배 확대 · 축소
    scaleY(sy)	    y축으로 sy배 확대 · 축소
    rotate(각도)	    회전(단위 : deg, rad 등)
    skew(ax, ay)	    x축, y축으로 왜곡(비틀기)
    skewX(ax)	    x축으로 왜곡
    skewY(ay)	    y축으로 왜곡

### Transition

__CSS 속성 변화를 위한 명령__

    transition-property
            all	모든 속성
            none	아무것도 바뀌지 않음
            (속성이름)	특정 속성만 바뀜
            -> width, height, etc

    transition-duration	실행 시간
            (시간)	특정 시간동안 진행됨

    transition-timing-function	속도 곡선
            linear	일정 속도
            ease	느림-빠름-느림(기본값)
            ease-in	느린 시작
            ease-out	느린 끝
            ease-in-out	느린 시작, 느린 끝
            cubic-bezier(n, n, n, n)	베지어 함수(데모)
            transition-delay	(시간)	특정 시간 후 트랜지션

    ex) .box {
            transition
        }
        .box:hover{
            width: 200px;
            height: 200px;
            background-color: #f50;
            transform: rotate(270deg);
        }
    + opacity: 요소의 불투명도. transition에서 많이 사용

### Animation

    animation-name          애니메이션 이름(Keyframe이름)
    animation-duration      애니메이션 실행시간
    @keyframes              애니메이션지점

    animation-direction	(방향)
            normal	        실행 후 원위치(기본값)
            alternate	실행 후 되돌아가기 실행

    animation-iteration-count	반복횟수
            (숫자)	        숫자만큼 반복
            infinite	무한 반복

    animation-time-function	속도곡선
            linear	                    일정 속도
            ease	                    느림-빠름-느림(기본값)
            ease-in	                    느린 시작
            ease-out	            느린 끝
            ease-in-out	            느린 시작, 느린 끝
            cubic-bezier(n, n, n, n)    베지어 함수(데모)

    animation	        한꺼번에 지정

__Example__

    #container {
    border: 1px solid transparent;
    animation-name: shape
    animation-duration: 3s;
    }
    @keyframes shape {
    from { border: 1px solid transparent; }
    to { border: 1px solid #000;
        border-radius: 50%;}
    }


