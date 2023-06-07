## Mission-02

[html 리뷰](#html-리뷰)  

[CSS](#CSS)
[접근성](#접근성)
[초기화](#초기화)
[로그인 섹션](#로그인-섹션)
[버튼 설정](#버튼-설정)
[회원 가입, 아이디 비밀번호 찾기 링크](#회원-가입-아이디-비밀번호-찾기-링크)
[가로선 설정](#가로선-설정)


### html

- 클래스 네이밍은 최대한 BEM 형식으로 함
- 시맨틱 태그 aside > section 태그 사용
```
<aside>
  <section class="login">
  <!-- ... -->
  </section>
<aside>
```

- section 태그에 제목으로 h3 태그 삽입
```
<h3 class="loginTitle">로그인</h3>
```

- 로그인을 위해 form 태그 생성
- form 태그 안에 fieldset, legend, label, input 태그 삽입
- label과 input 태그, for과 id로 묶어 줌.
- input 태그에 required 삽입
- input password 타입에는 minlength로 8자리 이상 입력 체크하도록 함
```
<form action="" method="post" id="login_form" class="loginForm">
  <fieldset class="login__Fieldset">
    <legend>로그인</legend>
    <!-- ... -->
      <label for="euidPw" class="login__label">비밀번호</label>
      <input type="password" id="euidPw" placeholder="8자리 이상" minlength="8" class="login__input" required />
    <!-- ... -->
  </fieldset>
</form>
```

- 회원 가입 | 아이디, 비밀번호 찾기는 ul li 태그와 a 태그로 링크 생성
```
<ul class="login__linkList">
  <li><a href="https://yamoo9.github.io/front-end-master/account/register.html">회원가입</a></li>
  <li><a href="https://yamoo9.github.io/front-end-master/account/signin.html">아이디 비밀번호 찾기</a></li>
</ul>
```


### CSS

#### 접근성
```
.a11yHidden,
legend {
  overflow: hidden;
  position: absolute !important;
  clip: rect(0, 0, 0, 0);
  clip-path: inset(50%);
  width: 1px;
  height: 1px;
  margin: -1px;
}
```

#### 초기화
- 폰트
- 패딩, 마진, 보더 0
- input 에이전트 스타일 제거
- li 스타일 변경
- a 태그 스타일 초기화
- 자주 사용한 변수 설정(border-radius 값)
```
body {
  font: inherit;
  font-family: Pretendard, -apple-system, BlinkMacSystemFont, system-ui, Roboto,
    "Helvetica Neue", "Segoe UI", "Apple SD Gothic Neo", "Noto Sans KR",
    "Malgun Gothic", "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol",
    sans-serif;
  font-size: 13px;
}

body, ul, h3, fieldset {
  padding: 0;
  margin: 0;
}

ul li {
  list-style-type : square;
}

fieldset {
  border: 0;
}

input {
  -webkit-appearance: none;
  appearance: none;
}

a {
  text-decoration: none;
  color: #181818;
}

:root {
  --radius: 5px;
}
```

#### 로그인 섹션

- 전체 너비 및 패딩 값 설정
- 배경색 그래디언트, 그림자 효과 추가
- 섹션 타이틀 스타일
- 로그인 버튼 위치 조정 위해 부모 속성인 로그인 폼에 position relative 값 부여
- label 너비 고정을 위해 inline-block 속성 부여
- input 태그에 padding으로 크기 설정.
- 너비 변화에 유연히 대처 위해 width 값 px값 대신 % 부여

```
.login {
  width: 244px;
  padding: 12px;
  background: linear-gradient(to right, #ED552F, #E8852E);
  border-radius: var(--radius);
  box-sizing: border-box;
  box-shadow: 5px 5px gray;
}

.loginTitle {
  color: #FF0;
  padding-bottom: 10px;
}

.loginForm {
  position: relative;
  border-radius: var(--radius) var(--radius) 0 0;
  background-color: #fff;
}

.login__Fieldset {
  padding: 8px 8px 0 8px;
  border-radius: var(--radius);
}

.login__label {
  width: 25%;
  display: inline-block;
}

.login__input {
  width: 43%;
  border: #CCC solid 1px;
  border-radius: var(--radius);
  padding: 3px 0 3px 7px;
  margin-bottom: 4px;
  box-sizing: border-box;
}

```

#### 버튼 설정
- 로그인 버튼 위치 설정을 위해 position absolute 값 부여
- top, right로 위치 조정

```
.login__Btn {
  color: #fff;
  background-color: #ED552F;
  border: 0;
  border-radius: var(--radius);
  padding: 17px 5px;
  position: absolute;
  right: 10px;
  top: 8px;
  cursor: pointer;
}

```

#### 회원 가입, 아이디 비밀번호 찾기 링크
- ul li에 float 값 부여
- float 해제를 위해 부모 속성인 ul에 display flow-root 값 부여

```
.login__linkList {
  display: flow-root;
  padding: 10px;
  padding-top: 5px;
  border-radius: 0 0 var(--radius) var(--radius);
  background-color: #fff;
}

.login__linkList li:first-child {
  float: left;
  margin-left: 15px;
}

.login__linkList li:last-child {
  float: right;
}
```

#### 가로선 설정
- border 값을 주면 상하좌우에 적용이 되어 한 곳에만 1px 주도록 설정

```
hr {
  border-width: 1px 0 0 0;
  background-color: #CCC;
}
```