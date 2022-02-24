# Box

HTML에서는 정말 많은 요소들이 box 형태를 가지고 시작한다.  
이러한 box의 형태나 배치를 조절하기 위해 CSS에서는 어떻게 이 box에 스타일을 적용하는지 기초부터 알아보자.

## 🙋🏻 Box Model

<img width="996" alt="스크린샷 2022-02-24 오전 10 12 05" src="https://user-images.githubusercontent.com/86224851/155438040-8522c5b8-fb5a-461d-b30f-90051767b546.png">

box 형태는 위 그림과 같은 형태를 가진다. 가장 안쪽부터 살펴보자.

### Content

텍스트 등의 내용이 들어가는 부분으로, 가로를 width, 세로를 height라고 한다.

### Padding

content와 border 사이의 공간으로, 안쪽 여백을 의미한다.

### Border

box의 테두리를 나타낸다.  
굵기, 스타일, 색상을 꼭 입력해줘야하며 순서는 상관없다.  
ex) border : 1px solid #000;

추가적으로 border-radius라는 속성은 테두리의 모서리 부분을 둥글게 만들어준다. 이를 활용해 원을 만드는 작업이 가능하다. 속성값을 50%로 설정하면 원이 된다!

### Margin

요소와 요소 사이의 간격으로, 바깥 여백을 의미한다.

## CSS에서 어떻게 표현하지?

위에서 살펴본 box 형태의 세부사항은 어떻게 CSS에서 조작할 수 있을까?

하나의 box를 만들어서 예시를 만들겠다.

<img width="884" alt="스크린샷 2022-02-24 오전 11 17 42" src="https://user-images.githubusercontent.com/86224851/155444726-7abca3c8-6bd6-4d6d-9443-10259b7d451b.png">

저 box 요소에는 아래와 같은 스타일이 적용되어 있다.  
하나씩 살펴보자.

```css
.box {
  width: 300px;
  height: 200px;
  padding-top: 20px;
  border: 1px solid #212112;
  margin-top: 30px;
}
```

<img width="187" alt="스크린샷 2022-02-24 오전 11 19 03" src="https://user-images.githubusercontent.com/86224851/155444862-3761e920-6aa6-4a73-9892-323bc9fa1995.png">

width는 content의 가로 길이이고, height는 세로 길이이다. 개발자 도구를 통해 box 테두리 내부의 가로가 300px, 세로가 200px인 것을 확인할 수 있다.  
padding-top은 padding을 윗부분에만 적용하겠다는 것이다. 위 사진에서 텍스트가 box 위에 붙어있는게 아니라 20px만큼 떨어져 있는걸 볼 수 있다. 개발자 도구를 통해 top 부분에만 padding이 적용되어있는 것을 확인할 수 있다.  
border는 box 형태에 테두리를 만들어준다. 코드는 1px 두께의 실선을 #212121 색상으로 만들겠다는 의미이다. 위 사진을 보면 box가 실선의 테두리를 가진 것을 볼 수 있는데, 자동으로 생성된게 아니라 이 코드를 통해서 만들어진 것임을 알 수 있다. 개발자 도구를 보면 border에 1px이 표시된 것을 확인할 수 있다.
margin-top은 margin을 box 윗부분에만 적용하겠다는 것이다. box를 두 개로 만들어서 어떤 변화가 있는지 보자.

<img width="886" alt="스크린샷 2022-02-24 오전 11 37 34" src="https://user-images.githubusercontent.com/86224851/155446833-209fdd72-410a-4936-a995-a7aaa986dc2e.png">

위의 box는 페이지 상단과 30px만큼 떨어져 있고, 아래 box는 바로 위의 box와 30px만큼 떨어져있다. 개발자 도구를 보면 top 부분에만 margin이 적용된 것을 확인할 수 있다.

## 다양한 예시 + 속기법(shorthand)

속기법이란 CSS를 빠르게 작성하는 방법이다.  
예를들어, padding을 상하좌우에 전부 넣고싶다고 하자.  
padding-top, right, bottom, left를 하나씩 써주면 너무 귀찮다. 이를 padding 하나로 해결할 수 있다.  
속기법은 시계 방향으로 적용된다고 생각하면 쉽다.  
top -> right -> bottom -> left 순서로 적용이 된다.

```css
.box {
  padding: 10px 20px 30px 40px;
}
```

이는 top에는 10, right에는 20, bottom에는 30, left에는 40px의 padding을 적용한다.

```css
.box {
  padding: 20px 30px;
}
```

이는 top, bottom에는 20px의 padding이 right, left에는 30px의 padding이 적용된다.

```css
.box {
  padding: 10px 20px 30px;
}
```

이는 top에는 10, right에는 20, bottom에는 30px을 적용한다. 그렇다면 left는 0인 것일까?  
**아니다!** 속기법을 사용하게 되면 작성하지 않은 부분은 자동으로 대칭 방향에 있는 값을 사용한다.  
즉, 위 예시에서 left는 right의 값인 20px을 padding으로 사용한다.

이런 속기법은 top, right, bottom, left 각각을 따로 지정할 수 있는 속성에서 대부분 사용 가능하다.

예시를 몇 개 더 살펴보자.

```css
.box {
  width: 300px;
  height: 200px;
  padding: 10px 20px 30px 40px;
  background-color: hotpink;
  border-bottom: 2px solid #000;
  border-top-left-radius: 5px;
  border-bottom-right-radius: 5px;
  margin: 20px 40px;
}
```

가로는 300px, 세로는 200px.  
padding은 top부터 시계방향으로 10, 20, 30, 40px.  
배경 색상은 hotpink.  
border는 bottom 부분에만 2px의 #000 색상의 실선으로 생성.  
왼쪽 윗 부분과 오른쪽 아래 부분은 5px만큼 둥글게.  
margin은 top, bottom은 20, right, left는 40px.  
이를 웹 페이지에 표시하면 아래와 같다.

<img width="885" alt="스크린샷 2022-02-24 오후 12 34 31" src="https://user-images.githubusercontent.com/86224851/155453147-6a27f037-1d66-4339-8fcd-5387454047a6.png">

개발자 도구를 통해 의도대로 만들어졌는지 살펴보자.

<img width="198" alt="스크린샷 2022-02-24 오후 12 35 26" src="https://user-images.githubusercontent.com/86224851/155453240-e7ecb37e-37d7-423d-913f-96c1471c5be8.png">

코드 설명을 했던 것과 동일한 결과가 나온 것을 볼 수 있다.
