# html_basic

## SASS
### preprocessor SASS
- SASS 는 CSS에서 변수, 함수, import, 상속 등 프로그래밍 문법을 쉽게 사용할 수 있도록 도와주는 전처리언어(preprocessor) 중 하나이다
- SASS 세팅
    - extension에서 live sass compiler 설치(최신 버전으로)
    - main.scss 확장자로 sass file을 작성
    - 에디터 최하단 watch sass 를 클릭하면 live sass compiler 가 scss file을 찾아 css, css.map으로 변환해준다
    - 변환된 scss file은 스타일 작성 후 저장하면 자동으로 css에 반영된다

### css 프로그래밍 요소
```css
:root {
    --main-color : #2a4cb2;
}

.background {
    background-color: var(--main-color);
    font-size: calc(20px + 2px);
    width: calc(40% - 20px);
}
```
- css에서도 위와 같이 변수, 사칙 연산 등을 할 수 있다
    - :root {} 안에 변수 선언 후, var()를 이용해 스타일 값으로 사용할 수 있다
    - calc() 를 이용해 사칙 연산을 할 수 있는데, 특이한 것은 단위가 다른 % - px 같은 경우도 사용이 가능하다

### SASS 프로그래밍 요소
```scss
$main-color : #2a4cb2;
$sub-color: #eeeeee;
$base-size: 16px;

.background {
    background-color: $main-color;
    color: $sub-color;
    font-size: ($base-size + 2px);
    font-size: ($base-size / 2);
}
```
- scss 문법은 css 보다 조금 더 사용이 편리하다
- $변수명 : 값 으로 변수 선언이 가능하고 $변수명을 그대로 스타일 값에 사용할 수 있다
- 변수에는 모든 스타일 값들을 지정하여 사용할 수 있어 기준 사이즈 등을 정해놓고 상대적으로 모든 개체 사이즈를 지정해 줄 수 있는데, 이렇게 사용할 경우 전체 사이즈 수정이 필요할 때 기준 사이즈만 변경해주는 등 관리가 편리해진다
- 다만 css 처럼 단위가 다른 사칙 연산은 불가능하다