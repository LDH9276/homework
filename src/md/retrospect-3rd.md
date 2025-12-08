# 세 번째 회고

## CSS 선택자의 이해

이번주는 CSS 선택자 위주와, CSS에 적용 방식에 대해 배웠다.
특히 전역변수 `:root`는 다양한 방법과 변수를 씀으로서 유지 보수가
쉬워지는 것에 대해 알게 되었다.

```
@property --primary-color {
  syntax: "<color>";
  inherits: false;
  initial-value: rgb(121, 0, 36);
}

/* 전역 변수 */
:root{
  --main-color : gray;
  --default-color: pink;
}

.like{
  background: var(--base-color, var(--default-color, red));
}

.wrapper{
  --default-color: #ffcc;
  --primary-color: darkblue;

  border: 1px solid var(--main-color);
  background: var(--default-color);
  background: var(--default-color);

  color: var(--primary-color);
  margin-block: 20px;

  .euid{
    color: var(--primary-color);
  }
}
```

또 가장 유용하게 배운 것은 '논리 속성과 논리 값'이었다.
그동안 margin-bottom 등 다양한 값을 썼지만

```
.bootcamp {
  position: relative;
  background: #cff;
  inline-size: 300px;
  block-size: 100px;

  strong {
    position: absolute;
    background: #fcf;
    /* inset-inline-start: 0;
    inset-inline-end: 0;
    inset-block-start: 0;
    inset-block-end: 0; */
    inset: 0;
  }
}

.frontend{
  background: #cff;

  strong{
    float: inline-start;
    background: yellowgreen;
  }
}

.euid{
  padding: 10px;
  border-bottom: 1px solid #ddd;
  background: salmon;
}
```

으로 간격 등 다양한 언어, 예를 들면 아랍권 환경에서도 큰 문제 없이 작동되는 것을 알게 되었다.
또한 flex 속성인데

```
  /* flex 값은 glow, basis, shrink*/
  flex: 1 0 0;

  /* 기준값을 주지 않으면 auto, 컨텐츠에 따라 길이 조절 */
  /* flex-basis: 0; */

  /* basis, glow값 없다면 아이템이 클 경우, 내부적으로 맞추어 축소시킨다. */
  inline-size: 250px;

  /*
  반응형 레이아웃에서
  glow와 basis shrink를 적절하게 쓰면 편하다.
  세 값은 gap도 포함이 된다. (width 값을 주지 않아도 된다.)
  */

  /* 이렇게 각각 glow를 주면 레이아웃이 깨지지 않는다. */
  /* .school-item1{
    flex-grow: 1;
  }
  .school-item2{
    flex-grow: 2;
  }
  .school-item3{
    flex-grow: 3;
  }
  .school-item4{
    flex-grow: 4;
  } */
```

으로 flex만으로 레이아웃을 짤 때 basis, glow로
**동적인 레이아웃**을 짤 수 있어 향후 프로젝트를 만들 때
해당 부분을 집중적으로 사용해볼 생각이다.

가장 이번주에 크게 배운 것은
float 였는데, **display 인라인과 블록 속성에 따라 float 레이아웃이** 바꾼다는 생각을 하지 않고 무작정 float로만 썼는데
이는 나중에 태그 변경 등으로 레이아웃의 변하는 일이 있어 사용할 때 신중해야 되겠다라고
작업하면서 느꼈다.

아래는 그 예시다.

```
  /* display속성이 block을 지정하면 float가 필요하다. 즉, inline, inline-block도 float 걸어두면 유지관리에서 유용하다. */
  .term-subject,
  .term-description{
    display: block;
    float: inline-end;
    width: calc(100% - 76px);
  }
  .term-thumbnail{
    float: inline-start;
  }
```

이 부분을 가장 많이 배웠던 것 같다.
앞으로도 유지보수 측면에서도 display 속성을 통해
레이아웃에 대해 생각해 볼 시간이었던 것 같다.

## 향후 수업의 집중할 내용

플랙스, 플로트 속성을 통해 레이아웃 배치에 대한 이해도를 쌓는
한주였던 것 같다. 향후 속성을 더 연습해보고
다른 프로젝트에 적용해 퍼블리셔적 관점이 아닌
논리적으로 생각하며 레아이웃을 구현하는 시각을 가져야 할 것 같다.
