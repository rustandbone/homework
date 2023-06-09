## Mission-03

![구현-스크린샷](./mission-03.gif)

- [Mission-03](#mission-03)
  - [html](#html)
  - [CSS](#css)
    - [접근성](#접근성)
    - [초기화](#초기화)
    - [공통 요소](#공통-요소)
    - [사이트 섹션 설정](#사이트-섹션-설정)
    - [섹션 제목](#섹션-제목)
    - [사이트 목록](#사이트-목록)
    - [호버 효과](#호버-효과)

### html

- 클래스 네이밍은 최대한 BEM 형식으로 함
- 시맨틱 태그 aside > section 태그 사용
```
<aside>
  <section class="site">
  <!-- ... -->
  </section>
<aside>
```

- section 태그에 제목으로 h3 태그 삽입
- 부분 색깔을 주기 위해 span 태그로 묶음
```
<h3 class="siteTitle">
  관련 <span class="siteTitle__span">사이트</span>
</h3>
```

- 사이트 목록이므로 ul li 태그 사용, 링크 태그 삽입
```
  <ul class="site__lists">
    <li class="site__list">
      <a href="https://zero-base.co.kr/">제로베이스</a>
    </li>
    <!-- ... -->
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
- 패딩, 마진 0
- li 스타일 제거
- a 태그 스타일 설정
```
body {
  font: inherit;
  font-family: Pretendard, -apple-system, BlinkMacSystemFont, system-ui, Roboto,
    "Helvetica Neue", "Segoe UI", "Apple SD Gothic Neo", "Noto Sans KR",
    "Malgun Gothic", "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol",
    sans-serif;
  font-size: 13px;
  color: #181818;
}

body, ul, h3 {
  padding: 0;
  margin: 0;
}

ul li {
  list-style-type : none;
}

a {
  text-decoration: none;
  color: #181818;
  display: block;
}
```

#### 공통 요소
- section과 ul 태그에 공통으로 적용되는 요소(보더 및 radius) 묶어서 적용
- 패딩, 보더 값이 너비 안에 잡히도록 border-box 설정
```
.site, .site__lists {
  border: 1px solid #A3A3A3;
  border-radius: 5px;
  box-sizing: border-box;
}
```

#### 사이트 섹션 설정
- width 값 설정
- 배경 그라이언트 값 설정
```
.site {
  width: 190px;
  background: linear-gradient(#CCC, #EEE);
  padding: 8px 12px 12px;
}
```

#### 섹션 제목
- 패딩 값 설정
- 제목 일부 span으로 색깔 설정
```
.siteTitle {
  padding-bottom: 10px;
}

.siteTitle__span {
  color: #ED552F;
}
```

#### 사이트 목록
- height 기본 값 설정
- 배경, 패딩 설정
- 트랜지션으로 높이, 패딩 값 변하도록 설정
- 높이는 즉각, 패딩은 0.5초 딜레이 후에 변하도록 설정
- 초기 height 값 넘치는 요소 보이지 않도록 overflow hidden 처리
```
.site__lists {
  height: 27px;
  background-color: #fff;
  padding-left: 30px;
  transition: height 700ms, padding 500ms 0.5s;
  overflow: hidden;
}
```

- 개별 사이트 목록 패딩 설정
- 첫 번째, 마지막 요소에는 다른 패딩 값 설정
```
.site__list {
  padding-bottom: 10px;
}

.site__list:first-child {
  padding-top: 5px;
}

.site__list:last-child {
  padding-bottom: 5px;
}
```


#### 호버 효과
- ul에 마우스 올릴 때 변동될 값 설정(높이, 패딩)
```
.site__lists:hover {
  height: 145PX;
  padding-top: 10px;
  padding-bottom: 10px;
}
```