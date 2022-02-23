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

## 🙋🏻 Structural Pseudo-classes

구조적 가상 클래스.  
가상 클래스란 어떤 상태나 조건을 만족했을 때 사용되는 클래스.  
다음과 같은 HTML 코드가 있다고 하자.

```html
<body>
  <section>
    <h1>Heading</h1>
    <ol>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
      <li>This is Cool~~</li>
    </ol>
  </section>
</body>
```

길게 나열된 리스트 태그에서 특정한 번호의 리스트를 선택하고자 한다.  
가장 첫번 째의 태그를 선택하고 싶다면 어떻게 해야할까?

```css
li:first-child {
  color: blue;
}
```

"요소:first-child" 라고 입력하면 요소의 배열 중 가장 첫번 째 요소를 선택할 수 있다.  
결과를 확인해보자.

<img width="148" alt="스크린샷 2022-02-22 오후 7 12 20" src="https://user-images.githubusercontent.com/86224851/155110928-a08e29f5-3d0a-4f40-b106-43bba12ba227.png">

나열된 li 태그 중 가장 첫번 째 태그만 스타일이 적용된 것을 확인할 수 있다.

그렇다면 가장 끝에 있는 요소를 선택할 수도 있을까?  
가능하다!

```css
li:last-child {
  color: red;
}
```

"요소:last-child" 라고 입력하면 요소의 배열 중 가장 마지막에 있는 요소를 선택할 수 있다.  
결과를 확인해보자.

<img width="146" alt="스크린샷 2022-02-22 오후 7 20 31" src="https://user-images.githubusercontent.com/86224851/155112308-59f4ce4b-dbff-4636-bd64-c5d606a53092.png">

가장 마지막 li 태그만 스타일이 적용된 것을 확인할 수 있다.  
그렇다면..처음과 끝 말고는 선택할 수 있는 방법이 없을까? 있다!

"요소:nth-child(n)"를 사용하면 된다!

```css
li:nth-child(3) {
  color: green;
}
```

li 태그 중에 3번째인 것을 선택하겠다는 뜻이다.  
결과를 살펴보자.

<img width="145" alt="스크린샷 2022-02-23 오전 10 12 22" src="https://user-images.githubusercontent.com/86224851/155246420-217589ff-b6e4-4a97-9cc8-f2c72276d389.png">

3번째 li만 색상이 변경된 것을 볼 수 있다.  
물론 n에 1 ~ 끝번호 까지 넣을 수 있지만, 첫과 끝은 보통 first, last-child를 사용하므로 잘 쓰지는 않는다.  
n을 활용하여 다양한 방법으로 사용할 수 있는데, 가령 예를들어, 짝수 번호만 선택하고 싶다면 2n을 입력하면 된다.

```css
li:nth-child(2n) {
  color: yellow;
}
```

<img width="146" alt="스크린샷 2022-02-23 오전 10 16 22" src="https://user-images.githubusercontent.com/86224851/155246733-d9c4fab2-2f8d-46f4-8984-7c0c12fbb424.png">

짝수 번호 2,4번 태그만 색상이 변경된 것을 확인할 수 있다.  
홀수 번호만 선택하려면 2n-1,2n+1 등 다양한 방법이 있다.  
짝,홀뿐만 아니라 n을 활용한 식을 넣어서 지정해줄 수도 있다.

## 🙋🏻 User Action Pseudo-classes

유저의 특정 움직임에 따라 가상 클래스를 활용할 수 있다.  
아래와 같은 HTML이 있다고 하자.

```html
<body>
  <section>
    <h1>Heading</h1>
    <a href="#">Kitube Channel</a>
    <input type="email" placeholder="Enter your email" />
  </section>
</body>
```

## hover

만약 유저가 태그 위에 마우스를 올려놓게 됐을 때, 태그의 색상이 변경되도록 만들고싶다면 hover를 사용한다.

```css
a:hover {
  background-color: hotpink;
}
```

<img src="https://user-images.githubusercontent.com/86224851/155247628-ac2ef78d-37b3-49c1-9913-9d9636c63463.gif">

## active

만약 유저가 태그를 누르는 그 찰나, 그 순간에 대한 class를 사용하고 싶다면 active를 사용하면 된다.

```css
a:active {
  background-color: indianred;
}
```

<img src="https://user-images.githubusercontent.com/86224851/155247860-d503d0c4-c2e6-49c2-ac86-bc3684fbd6bd.gif">

여기서 주의할 점은 유저가 마우스를 누르기만 하고 떼지 않았다면 계속 active 상태를 유지한다는 것이다!  
마우스를 떼야지 active 상태가 해제된다.

## focus

만약 유저가 태그를 눌러서 활성화 상태로 만들었을 때를 class로 사용하고 싶다면 focus를 사용하면 된다.

```css
input:focus {
  border: 3px tomato solid;
}
```

<img src="https://user-images.githubusercontent.com/86224851/155248539-c193a953-0c7a-4384-87cf-5ef7f09539f4.gif">

유저가 input 태그를 클릭해서 무언가를 입력할 수 있게 만들어 놨을 때 테두리 색상이 변경되는 것을 볼 수 있다.

## 🙋🏻 CSS Selectors Olympic

위에서 다양한 선택자에 대하여 알아보았다.  
그런데 중복 선택된 요소들 중에 어떤 스타일이 덮여쓰여지는가에 대해서는 자세하게 설명하지 않았다.  
이번엔 어떤 선택자에 의해 선택되는 것이 더 우선 순위를 가지는지를 다양한 예시를 올림픽 메달에 비교해서 설명해보겠다.

```css
/*누가 적용될까?*/
p {
  color: blue;
}

p {
  color: hotpink;
}
```

정답은 아래쪽 p 태그이다. CSS(Cascading Style Sheet)는 아래로 내려가면서 적용되기 때문에 같은 요소를 지정한 것이 있다면 더 아래쪽에 있는 것이 적용된다!

정말 기초적인 CSS 작동 순서를 알았으니 심화 단계로 가자.  
나는 올림픽 메달에 비교하여 설명을 진행하고자 한다.  
올림픽에서는 금메달, 은메달, 동메달이 있고 높은 순위의 메달이 많을수록 해당 국가는 더 높은 점수를 얻게 된다.  
또한 점수의 크기가 금 >> 은 >> 동 이므로, 금메달이 하나 있다면 은메달이 아무리 많아도 이길 수가 없다.  
각 메달에 해당하는 선택자는 다음과 같다.

금메달 : ID  
은메달 : Class, Pseudo-class  
동메달 : Type

아래와 같은 HTML 문서가 있다고 하자.

```html
<body>
  <p id="text" class="a b c d e f g h i j k l m n o">Goodbye My yesterday</p>
</body>
```

과연 하나의 ID와 십수개의 class를 동시에 스타일 설정을 하면 어떻게 될까?

```css
#text {
  color: blue;
}

.a.b.c.d.e.f.g.h.i.j.k.l.m.n.o {
  color: red;
}
```

정답은 **ID가 적용된다**이다.  
아무리 많은 class 지정자를 사용한다고해도 하나의 ID 지정자를 이길 수가 없다.

다음 예시를 보자.
과연 누가 우선 적용될까?

```css
.box p {
  color: blue;
}

p {
  color: hotpink;
}
```

정답은 **.box p**이다.  
.box p는 은메달 1개, 동메달 1개이다.  
반면, p는 동메달 1개이다.  
따라서 .box p가 우선 적용되는 것이다!

슬슬 복잡해지기 시작한다.  
점수 합산 방식을 연습해보자!

```css
/*금메달 1개, 은메달 1개*/
#gnb.tab-nav {
  color: blue;
}

/*은메달 1개, 동메달 1개*/
header.main-header {
  color: red;
}

/*금메달 1개, 은메달 1개, 동메달 1개*/
#gnb.tab-nav ul {
  color: black;
}

/*금메달 1개, 은메달 2개, 동메달 1개*/
#gnb.tab-nav ul:last-child {
  color: white;
}
```

나중에 내가 CSS를 작성했는데 적용이 안된다면, 이 점수 합산을 통해서 덮어버리는 선택자가 있는지를 체크하는게 좋을 것이다!

### 그런데...

이런 점수 합산 방식을 부숴버리는 Rule Breakers가 있다!

첫 째로는, inline Style이 있다.  
이는 HTML 문서에서 태그 내에 style 속성으로 직접 지정해놓은 스타일을 말한다.

```html
<body>
  <p id="text" style="color: red">Hi</p>
</body>
```

```css
#text {
  color: blue;
}
```

ID 선택자와 inline Style을 동시에 적용해보았다. 과연 어떤 스타일이 적용될까?  
정답은 **inline Style**이다.  
점수가 높은 선택자를 아무리 사용해도 inline Style을 이길 수가 없다...

그런데 inline Style보다 강한 녀석이 있다...!  
바로, !important이다.  
바로 위에 있는 HTML과 같은 상황에서 CSS는 아래와 같다고 하자.

```css
p {
  color: yellow !important;
}
```

이렇게 되면 inline Style이 지정되어있더라도 !important가 있는 것이 덮여진다!!

이렇게 Rule Breakers까지도 알아보았다.  
이 친구들은 웬만하면 사용하지말자...  
디버깅할 때 굉장히 곤란한 상황을 만들기 때문이다..

이로써 CSS Selectors에 관한 공부를 마치도록 하겠다.  
🥳 수고하셨습니다~
