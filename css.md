# 선언방식

> 내장방식 : head안에 style 태그 사용

> 인라인방식 : `<div style="color: red; margin: 20px;"></div>`

> 링크방식 : `<link rel="stylesheet" href="./css/main.css"> (병렬방식)`

> import방식 : 링크방식으로 연결되어있는 css파일에 @import url("./box.css");를 입력해서 html파일과 연결되어있는 main.css에 box.css를 연결하는 방식 (직렬연결)

# 선택자

> 전체 선택자 : \* {color: red;}

> 태그 선택자 : div {margin: 100px;}

> 클래스 선택자 : `.class {color: red;}`

> 아이디 선택자 : `#id {color: red;}`

> 복합 선택자
>
> > 일치 선택자 : `span.orange{color: red;}` : span태그와 orange클래스 모두 만족시키는 선택자
> >
> > 자식 선택자 : `ul > .orange{color: red;}` : 자손 X, 자식 O
> >
> > 하위 선택자 : `div .orange{color: red;}` : 부모,자식 관계와 상위 하위 관계를 이해하면 됨
> >
> > 인접 형제 선택자 : 같은 부모를 공유하는 요소들 중 다음 요소
> > `.orange + li{color: red;}` : orange클래스가 있는 요소 다음에 li요소들 중 '하나'(가장 인접한)
> >
> > 일반 형제 선택자 : `.orange ~ li{color: red;}` : orange클래스가 있는 요소 다음에 li요소들 '모두'(하나x)

# 가상 클래스 선택자

어떠한 행동을 했을 때 동작하는 개념(js같은 기능)

```md
1.  :hover : 요소에 마우스 '커서가 올라가 있는 동안' 선택
    .box{
    width : 100px;
    height : 100px;
    background-color: orange;
    transition: 1s; / hover이 반응하는데 1초가 걸리도록 하는 명령어
    }
    .box:hover {
    width: 300px;
    background-color: royalblue;
    }
    .box의 영역에 마우스 커서를 갖다대면 1초 동안 폭이 300으로 증가하며 색상이 블루로 바뀜

2.  :active : 요소에 마우스를 '클릭하는 동안' 선택

3.  :focus : input와 같은 focus가 가능한 테그가 한정이지만, div와 같은 포커스가 불가능한
    태그에 tapindex="-1"을 입력하면 포커스 가능 / 포커스는 클릭과는 다른 개념이다
4.  first-child / (last-child는 마지막)
    ex) .fruits div:first-child{color: red;} : fruit라는 클래스를 가진 태그 내의 하위
    태그들 중 div가 첫번째로 오는 경우 적용됨 / div:first-child는 일치 선택자이므로 div와
    first-child 모두 만족해야함
5.  .fruits *:nth-child(2) {color: red;} : fruits클래스를 가진 태그 중 n번째를 선택 /
    *라서 모든 태그
    .fruits \*:nth-child(2n) {color: red;} : fruits클래스를 가진 태그 중 2배수를 선택 /
    0부터 카운팅
    (2n+1, n+2 등등 응용 가능)
6.  부정선택자
    .fruit \*:not(span) {color: red;} : fruit 클래스를 가진 태그들 중 span태그만 제외
```

# 가상 요소 선택자

content라는 명령어만 사용 가능 / 블록이 아닌 인라인 요소

```md
.box::before {content: "앞!"} : box클래스 내부 앞에 내용을 삽입
.box::after {content: "뒤!"} : box클래스 내부 뒤에 내용을 삽입
```

# 속성 선택자

```md
<input type="text" value="ABCD" disabled /> 요소는 type, value, disabled라는 속성을 가질 때

[disabled or value or type] {
color: red;
}

[type="text"] {
color: red;
}
```
