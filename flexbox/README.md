# 🤪 Flex box

복잡하디 복잡한 float을 배우고 여기까지 왔다.  
최근에는 float보다는 flex를 더 많이 사용하는 추세라고 한다.  
그치만 예전 코드를 수정하는 작업을 하기 위해서는 반드시 두 개념 모두를 알아야기 때문에 공부는 잘해놓자 ㅎㅎ..

flex는 정렬의 끝판왕이다.  
그의 특징들을 먼저 살펴보자.

## 1. 나, 플레스 박스 쓸거임(단호)

flexbox를 사용하려면 정렬하고자하는 요소의 "부모 요소"에 **display: flex;** 를 선언해야한다.  
flex와 inline-flex를 사용할 수 있는데,  
flex는 block과 비슷하지만 block에서는 할 수 없는 기능을 가지고 있고,  
inline-flex는 inline-block과 비슷하지만 inline-block이 할 수 없는 기능을 가지고 있다.

## 2. 가로 정렬? 세로 정렬?

다음으로는 어느 방향으로 정렬할 건지 알려줘야한다.  
이 때 사용되는 속성이 **flex-direction**이다.  
row(가로), row-reverse, column(세로), column-reverse 값을 사용할 수 있다.  
여기서 같이 등장하는 개념이 axis이다. flex-direction을 사용하면 생기는 가상의 축을 말한다.  
flex-direction으로 지정한 방향에 따라 main axis, cross axis가 생긴다.  
row일 때는 가로, column일 때는 세로가 main axis가 된다.  
row 값을 사용한다면 main axis는 왼쪽에서 오른쪽, cross axis는 위에서 아래가 된다.  
column 값을 사용한다면 main axis는 위에서 아래, cross axis는 왼쪽에서 오른쪽이 된다.  
그렇다면 reverse가 붙는 속성들은 어떻게 될까?  
다 똑같은데 main axis의 방향만 바뀐다.  
row-reverse는 main axis가 오른쪽에서 왼쪽이 되고, column-reverse는 main axis가 아래에서 위가 된다.  
두 속성 모두 cross axis는 변함이 없다.

## 3. 무조건 한 줄 안에 다 정렬??

다음으로는 요소들을 한 줄안에 전부 낑겨 넣을 것인지 말지를 정해줘야한다.  
이 때 사용하는 것이 **flex-wrap**이라는 속성이다.  
이 속성은 어떻게든 한 줄에 모든 요소를 정렬할 것인지, 아니면 상황에 따라 여러 줄에 정렬할 것인지를 정해준다.  
사용할 수 있는 값으로는 nowrap과 wrap이 있다.  
nowrap은 감싸지(wrap)않고 자식의 사이즈를 강제로 줄여서라도 한 줄로 정렬해버린다.  
예를들어, 부모의 width가 600px이고 자식요소 3개의 width가 각각 300px일 때, 원래대로면 한 줄에 두 개 이상의 자식요소가 들어갈 수 없지만 어떻게든 3개의 요소를 600px 안에 넣어버린다.  
이런 것은 float에서는 상상도 할 수 없었던 일이다!!  
wrap은 한 줄에 모두 정렬하기에 공간이 마땅치 않으면 여러 줄을 만들어서 정렬한다.

## 예시

위에서 살펴본 내용을 예시를 통해 더 자세하게 알아보자.  
사용할 HTML은 다음과 같다.

```html
<body>
  <div class="parent">
    <div class="child red">child</div>
    <div class="child yellow">child</div>
    <div class="child blue">child</div>
  </div>
</body>
```

가장 기본적인 flex-direction부터 살펴보자.

```css
.parent {
  display: flex;
  flex-direction: row;
}
```

3개의 .child를 flexbox로 활용하기 위해 부모 요소인 .parent에 **dispaly:flex;** 를 입력했다.  
flex-direction이 row이므로 가로축이 main axis이며 방향은 왼쪽에서 오른쪽이다.  
main axis에서의 정렬은 **justify-content** 속성을 사용한다.

## 🤔 justify-content

justify-content 속성에서 사용할 수 있는 값은 flex-start, flex-end, center, space-between, space-around가 있다.  
flex-start는 시작 부분으로 전부 정렬된다.  
예를들어, flex-direction이 row라면 왼쪽으로, row-reverse라면 오른쪽으로 정렬된다.

```css
.parent {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
```

아래 화면은 flex-direction이 row일 때의 결과이다. .red, .yellow, .blue가 순차적으로 왼쪽에서 오른쪽으로 정렬되는 것을 확인 할 수 있다.  
또한, justify-content가 center 값을 가지므로 자식 요소들이 부모 요소의 가운데에 정렬된 것을 확인할 수 있다.

<img width="1036" alt="스크린샷 2022-03-07 오전 9 50 47" src="https://user-images.githubusercontent.com/86224851/156950352-1500fcf4-4d7f-476a-9b19-95bd0d7a1162.png">

이번에는 flex-start 값을 알아보자.  
이 값은 start라는 단어를 보면 알 수 있듯이 부모 요소의 시작 부분, 가장 앞 부분으로 전부 정렬이 된다.  
row는 main axis가 왼쪽에서 오른쪽을 향하므로, 시작 부분인 왼쪽에 몰려서 정렬이 되는 것을 확인 할 수 있다.

```css
.parent {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
}
```

<img width="1015" alt="스크린샷 2022-03-07 오전 9 54 23" src="https://user-images.githubusercontent.com/86224851/156950528-c0f43932-d4c6-4ef5-8421-b306d10ec356.png">

이번에는 flex-end 값을 알아보자.  
이 값은 end라는 단어를 보면 알 수 있듯이 부모 요소의 끝 부분, 가장 뒷 부분으로 전부 정렬이 된다.  
row에서는 오른쪽이 끝부분이므로 오른쪽에 몰려서 정렬되는 것을 확인 할 수 있다.

```css
.parent {
  display: flex;
  flex-direction: row;
  justify-content: flex-end;
}
```

<img width="1020" alt="스크린샷 2022-03-07 오전 9 59 24" src="https://user-images.githubusercontent.com/86224851/156950801-be9a9275-9187-4029-a2df-66caa3cc8584.png">

이번에는 space-between 값을 알아보자.  
이 값은 요소들 사이의 간격을 일정하게 만들어서 정렬한다.

```css
.parent {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
```

<img width="1012" alt="스크린샷 2022-03-07 오전 10 01 50" src="https://user-images.githubusercontent.com/86224851/156950933-9b7b76af-6ca5-4252-aea0-4321ce368666.png">

이번에는 space-around 값을 알아보자.  
이 값은 요소들 각각의 앞 영(around)의 간격을 일정하게 만들어서 정렬한다.

```css
.parent {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
```

<img width="1014" alt="스크린샷 2022-03-07 오전 10 03 19" src="https://user-images.githubusercontent.com/86224851/156951006-9865511e-b6c7-4993-b287-ab0a466a97ff.png">

space-between, space-around를 조금 헷갈릴 수 있다.  
전자는 맨 앞, 맨 뒤 요소가 양 끝으로 붙는다.  
후자는 맨 앞, 맨 뒤 요소가 양 끝에 붙지않고 계산된 간격만큼 떨어져서 배치된다.  
요소와 요소를 기준으로 하느냐, 요소 하나의 양옆을 기준으로 하느냐가 다른 것이다.

만약 flex-direction을 column으로 설정하면 어떻게 될까?  
위에서 살펴본 것들이 수직 방향(위에서 아래)으로 발생한다고 생각하면 된다.

## 🤔 flex-wrap

flex-wrap 속성은 한 줄에 모든 요소를 정렬할지, 여러 줄에 정렬할지를 정한다.  
자세한 설명은 위에서 3번 특징으로 설명을 써놨기 때문에 생략하겠다.  
바로 예시를 보자.

```css
.parent {
  width: 600px;
  height: 400px;
  display: flex;
  flex-direction: row;
  flex-wrap: nowrap;
}

.child {
  width: 300px;
  height: 200px;
}
```

코드 상으로는 .child의 width가 300px이기 때문에 .parent의 width인 600px을 넘겨버려 한 줄에 표시가 안 될 것으로 보인다.  
여기서 flex-wrap에 nowrap을 사용하여 이를 한 줄에 넣는 것으로 설정했다.  
결과는 아래와 같다.

<img width="611" alt="스크린샷 2022-03-07 오전 11 51 54" src="https://user-images.githubusercontent.com/86224851/156959595-719f9b95-4802-41e7-9e41-7adc1d5fccbb.png">

원래는 width가 맞지않아 한 줄에 모두 표현될 수 없음에도 강제로 width를 줄여 한 줄에 낑겨 넣은 것을 확인 할 수 있다.  
그렇다면 wrap을 사용하면 어떨까?

```css
.parent {
  flex-wrap: wrap;
}
```

wrap을 사용하면 한 줄에 요소를 전부 넣을 수 없는 경우, 여러 줄을 만들어 정렬한다.

<img width="614" alt="스크린샷 2022-03-07 오전 11 57 22" src="https://user-images.githubusercontent.com/86224851/156960108-7f84411d-f9b2-452a-a697-578a229fa4f5.png">

flex-wrap은 cross axis 정렬과 연관이 있다.

이번에는 cross axis에서의 정렬을 알아보자.  
align-items, align-content 속성이 있다.  
먼저 align-items부터 알아보자.

## 🤔 align-items

align-items는 center, flex-start, flex-end 값을 사용한다.  
각각의 기능은 위에서 살펴본 것과 완전히 동일하다.  
다만, cross axis를 기준으로 정렬이 진행된다는 것을 알아 두자.  
간단한 예시 하나만 보겠다.

```css
.parent {
  display: flex;
  flex-direction: row;
  align-items: center;
}
```

flex-direction이 row이므로 가로축이 main axis이고 cross axis는 세로축(위에서 아래)이 된다.  
align-items가 center이므로 cross axis 기준으로 가운데로 정렬될 것이다.

<img width="1017" alt="스크린샷 2022-03-07 오전 10 18 00" src="https://user-images.githubusercontent.com/86224851/156951938-a1114050-823a-4c6c-be28-d4440f647b47.png">

세로축 기준으로 가운데에 정렬된 것을 확인 할 수 있다.  
그런데...왜 space-between, space-around는 사용하지 않는걸까?  
두 속성은 위에서 살펴봤듯 요소와 요소 사이의 간격을 만드는 속성이다. 그런데 cross axis를 기준으로 하는 정렬은 요소와 요소를 정렬하는 것이 목표가 아니기 때문이다.

## 🤔 align-content

align-content 또한 cross axis에서의 정렬 기능을하는 속성이다.  
그런데, align-content 속성이 유효하게 적용되려면, flex-wrap 속성에서 wrap 값을 사용해야한다.  
만약, wrap을 사용하면서 align-items를 사용하면 약간 이상한 형태로 정렬이 된다.  
바로 예시를 살펴보자.

```css
.parent {
  width: 600px;
  height: 1000px;
  display: flex;
  flex-direction: row;
  align-items: flex-start;
  flex-wrap: wrap;
}
```

align-items를 사용하면서 wrap을 사용한 결과이다.

<img width="409" alt="스크린샷 2022-03-07 오후 12 04 17" src="https://user-images.githubusercontent.com/86224851/156960772-97592ea3-8f79-4d06-913b-a3aebd644403.png">

wrap으로 인해 여러 줄이 된 것은 알겠는데, 줄 사이의 간격이 굉장히 넓어졌다.  
왜 이런 현상이 발생한 것일까?
align-items는 요소들이 놓여있는 하나하나의 줄(축이라고 생각하면 더 편할지도 모르겠다)을 기준으로 작용하고 있기 때문이다.  
따라서, 전체를 기준으로, 전체의 cross axis를 기준으로 요소를 정렬하고자 한다면 align-content를 사용해야하는 것이다.

```css
.parent {
  align-content: flex-start;
  flex-wrap: wrap;
}
```

<img width="411" alt="스크린샷 2022-03-07 오후 4 30 21" src="https://user-images.githubusercontent.com/86224851/156987005-987a30bf-bec7-4662-9918-1be27603842b.png">

align-content에 flex-start를 줘서 cross axis의 시작 부분(윗 부분)에 정렬될 수 있게 만들었다.  
바로 위 예시와 달라진 것이 align-items를 align-content로 바꾼 것 뿐인데 이상적으로 정렬이 되었다.(물론 align-items에서처럼 하고싶다면 할 말이 없다..)

하나하나의 줄이 아닌 전체의 큰 cross axis를 기준으로 모든 요소를 이동시키기 때문에 nowrap에서의 align-items처럼 사용 가능하다.  
또한, align-items에서는 사용할 수 없었던 space-between, space-around도 적용이 가능해졌다.  
물론, 이건 전체 cross axis를 기준으로 하기 때문에 가능한 것이다.

## 🤔 order

order는 flex를 사용할 때 이용 가능한 속성이다.  
뜻 그대로 요소의 순서를 지정한다.  
즉, 마크업한 요소의 순서를 그대로 따라가지않고 내가 순서를 맘대로 지정할 수 있다는 것이다.  
여태까지의 예시들은 .red, .yellow, .blue 순서로 마크업이 되어 있어서 그대로 그 순서를 가지고 출력이 된다.  
order를 활용해서 순서를 바꿔보자.

```css
.red {
  background-color: red;
  order: 3;
}

.yellow {
  background-color: yellow;
  order: 1;
}

.blue {
  background-color: blue;
  order: 2;
}
```

이번에는 .yellow, .blue, .red 순서로 바꿔보았다.  
결과를 살펴보자.

<img width="609" alt="스크린샷 2022-03-07 오후 4 43 46" src="https://user-images.githubusercontent.com/86224851/156988789-2a8b02d5-f84c-4def-9d78-5f262fdf037b.png">

order 값에 따라 순서가 변경된 것을 확인할 수 있다.

이로서 flex의 효과와 활용법에 대해서 알아보았다.  
🥳 수고하셨습니다.
