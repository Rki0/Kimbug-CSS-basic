# Selectors

HTML 문서를 꾸미기 위해 CSS에서는 어떻게 그 태그들을 지정하는지에 대해서 알아보자!

## 🙋🏻 Type, Class & ID Selectors

아래와 같은 HTML 코드가 있다고 하자.

```html
<body>
  <ol>
    <li>CSS Selectors study</li>
    <li class="one">CSS Selectors study</li>
    <li class="one three">CSS Selectors study</li>
    <li class="one three four" id="two">CSS Selectors study</li>
    <li>CSS Selectors study</li>
    <li>CSS Selectors study</li>
    <li>CSS Selectors study</li>
    <li>CSS Selectors study</li>
  </ol>
</body>
```

## Type

특정 태그를 꾸미고자 한다면, CSS에 태그 이름을 그대로 적어주면 그 태그를 선택하게 된다.  
아래 예시를 살펴보자.

```css
li {
  color: tomato;
}
```

li 태그 안에 있는 텍스트를 tomato 색상으로 바꾼다는 뜻이다. 그 결과는 아래와 같다.

<img width="168" alt="스크린샷 2022-02-22 오전 10 24 30" src="https://user-images.githubusercontent.com/86224851/155046383-bbb71b3d-7484-446f-88a4-dc9135cd9e2c.png">

모든 li 태그에 스타일이 적용된 것을 볼 수 있다.  
그러면...내가 원하는 태그에만 스타일을 적용하는 것은 안될까?  
그 때 일반적으로 사용되는 것이 Class & ID Selectors이다.

## Class & ID Selectors

2,3,4번 리스트에 있는 텍스트를 따로 선택해서 꾸미려고 한다. 이렇게 여러 태그에 한번에 스타일을 지정할 때는 보통 Class Selectors를 사용한다.  
Class는 여러 개의 태그에 중복 지정해줄 수 있으므로, 맨 위 HTML 코드와 같은 형태로 만들 수 있겠다.  
적용하려고하는 Class를 CSS에서 표현하면 아래와 같다.

```css
.one {
  color: blue;
}
```

Class가 one인 태그들의 텍스트 색깔을 blue로 바꾸겠다는 뜻이다.  
결과는 아래와 같다.

<img width="164" alt="스크린샷 2022-02-22 오전 10 46 20" src="https://user-images.githubusercontent.com/86224851/155048203-945a7e56-921c-41f1-9b88-531aa9b60269.png">

one이라는 Class로 지정한 2,3,4번 리스트의 텍스트만 blue 색상으로 변경된 것을 알 수 있다.

Class는 하나의 태그에 여러 개를 지정할 수 있는데, 위의 HTML 코드를 보면 알 수 있다.  
여러 개의 Class가 지정된 녀석들은 어떻게 스타일을 적용할까?

```css
.one.three {
  color: yellow;
}
```

Class에 one, three가 포함된 태그는 텍스트 색상을 yellow로 변경하겠다는 뜻이다.  
결과는 다음과 같다.

<img width="160" alt="스크린샷 2022-02-22 오전 11 01 22" src="https://user-images.githubusercontent.com/86224851/155049506-4bdf3d9b-f77c-448a-b1fd-bece5416aad8.png">

3,4번 리스트의 Class에 포함된 three 때문에 앞서 적용되었던 .one의 스타일이 덮혀버린 것을 확인할 수 있다.

### 🙅🏻 이 때! 주의할 점이 있다!

Class를 입력할 때, 띄어쓰기가 매우 중요하는 점이다!  
아래 코드는 같을까 다를까?

```css
.one.three {
  color: yellow;
}
/* 두 코드는 완전히 다르다! */
.one .three {
  color: yellow;
}
```

정답은 **다르다**이다. .one과 .three 사이에 띄어쓰기가 없을 때는 Class에 one과 three가 포함된 태그를 지정하지만, 띄어쓰기가 있다면?!  
그 때는 Class에 one이 있는 태그만 지정하게 되므로 주의하자!!

그렇다면 4번 리스트 Class에 있는 four를 추가로 더하면 어떻게 될까?

```css
.one.three.four {
  color: aqua;
}
```

<img width="163" alt="스크린샷 2022-02-22 오전 11 04 16" src="https://user-images.githubusercontent.com/86224851/155049750-ea3ccb98-41a5-4c3c-b843-b45d2981d4c7.png">

적용해보니 .one.three의 스타일이 덮혀버린 것을 확인할 수 있다!

그런데, 갑자기! 2번 리스트의 색깔만 바꾸고 싶어졌다!  
단 하나의 태그만을 특정하는 것은 ID Selectors를 사용하면 된다. ID는 문서 내에서 단 한번만 사용할 수 있기 때문이다.

```css
#two {
  color: greenyellow;
}
```

two라는 ID를 가진 태그의 텍스트 색상을 greenyellow로 바꾸겠다는 것이다.  
결과는 아래와 같다.

<img width="159" alt="스크린샷 2022-02-22 오전 11 08 11" src="https://user-images.githubusercontent.com/86224851/155050084-7b2bdb39-c1fa-44f8-8bb9-f89abe8515c3.png">

4번 리스트에 Class Selectors를 통해 적용된 스타일이 ID Selector에 의해 덮혀져서 적용된 것을 확인할 수 있다.

## 🙋🏻 Child, Descendant & Sibling Combinators

각각의 뜻은 이렇다.  
Child : 자식  
Descendant : 자손  
Sibling : 형제

아래와 같은 HTML 코드가 있다고하자.

```html
<body>
  <section>
    <h1>Heading</h1>
    <ul>
      <li>
        <h1>Heading in list item</h1>
        <p>p in list item</p>
      </li>
      <li>
        <h1>Heading in list item</h1>
        <p>p in list item</p>
      </li>
    </ul>
  </section>
</body>
```

몇 가지 예시로 뜻을 이해해보자.

section의 자식

- h1
- ul

section의 자손

- section의 자식
- li
- li 내부 태그

ul의 자식

- li

ul의 자손

- ul의 자식
- h1
- p

ul의 형제

- h1(section의 자식)

h1(li의 자식)의 형제

- p

## 자손 요소 선택(Descendant)

section의 자손 요소 중 h1 태그를 모두 선택하려면 아래와 같은 코드를 사용한다.

```css
section h1 {
  color: tomato;
}
```

중요한 것은 선택자 사이에 **공백**이 존재한다는 것이다.  
공백을 넣어줘야 자손 요소를 선택하는 것이라는 것을 CSS에 알려줄 수 있는 것이다!

<img width="270" alt="스크린샷 2022-02-22 오전 11 47 33" src="https://user-images.githubusercontent.com/86224851/155053866-d257ad44-d7b9-4779-be1e-fb036fcc042a.png">

결과를 보면 section 태그의 자손으로 존재하는 모든 h1 태그가 선택되어 텍스트 색상이 변경된 것을 확인할 수 있다.

## 자식 요소 선택(Child)

그렇다면 section의 자식 요소인 h1 태그만 선택하려면 어떻게 해야할까?  
그럴 때는 꺾쇠(>)를 사용하면 된다. 예시를 보자.

```css
section > h1 {
  color: blue;
}
```

태그와 태그 사이에 꺾쇠(>) 표시가 있는 것이 보인다.  
section의 자식 요소에 있는 h1 태그만을 선택한다는 것이다.

<img width="259" alt="스크린샷 2022-02-22 오전 11 52 18" src="https://user-images.githubusercontent.com/86224851/155054357-8b4de47f-94f2-4be0-b865-58a6f1b30d39.png">

결과를 보면, section 태그의 직계 자식 요소 h1 태그만이 선택되어 텍스트 색상이 변경된 것을 확인할 수 있다.

## 형제 요소 선택(Sibling)

다음과 같은 HTML 코드가 있다고 생각하자.

```html
<body>
  <section>
    <h1>Heading</h1>
    <ul>
      <li>This is Cool~~</li>
      <li class="active">This is Cool~~</li>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
    </ul>
  </section>
</body>
```

.active에는 보다 다은 설명을 위해 font-weight을 700으로 설정해주고 시작하겠다.

형제 요소 선택에 쓰이는 기호는 두 가지가 있다.  
첫 째, ~ 기호이다. 사용법은 아래와 같다.

```css
.active ~ li {
  color: blue;
}
```

.active 다음의 형제 요소 li 태그부터는 전부 해당 스타일을 적용하겠다는 뜻이다.

<img width="158" alt="스크린샷 2022-02-22 오후 12 04 22" src="https://user-images.githubusercontent.com/86224851/155055566-2cc109a7-490f-4bea-956b-7305faad8b5f.png">

따라서 3 ~ 5번 형제 li 태그에 전부 스타일이 적용된 것을 확인할 수 있다.

둘 째, + 기호이다. 사용법은 아래와 같다.

```css
.active + li {
  color: tomato;
}
```

.active 바로 다음의 형제 li 태그에만 스타일을 적용하겠다는 뜻이다.

<img width="152" alt="스크린샷 2022-02-22 오후 12 06 36" src="https://user-images.githubusercontent.com/86224851/155055756-f77a272b-1967-4e5e-9e89-b6875abd669c.png">

결과를 보면 3번째 형제 li 태그에만 스타일이 덮여진 것을 확인할 수 있다.
