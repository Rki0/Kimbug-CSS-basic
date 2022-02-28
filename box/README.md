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

## 🙋🏻 Box Sizing

앞서 우린 아래와 같은 box model을 공부했다.

<img width="996" alt="스크린샷 2022-02-24 오전 10 12 05" src="https://user-images.githubusercontent.com/86224851/155438040-8522c5b8-fb5a-461d-b30f-90051767b546.png">

만약 내가 width가 480px, height가 480px, padding-top이 40px, padding-left가 50px인 box를 만들고자한다면 당연하게도 아래와 같이 코딩을 할 것이다.

```css
.box {
  width: 480px;
  height: 480px;
  padding-top: 40px;
  padding-left: 50px;
}
```

과연 내가 원하는대로 480px 정사각형 box가 생성되었을까?  
개발자 도구로 확인해보자.

<img width="180" alt="스크린샷 2022-02-25 오후 7 08 38" src="https://user-images.githubusercontent.com/86224851/155696561-3e99398e-7b8b-4b58-ab93-8ca3d3abfe40.png">

<img width="176" alt="스크린샷 2022-02-25 오후 7 09 16" src="https://user-images.githubusercontent.com/86224851/155696679-4f45daa5-867a-42b5-92f3-36e7af01dd06.png">

**원하는대로 나오지않았다.**  
입력했던 width, height는 content 부분에 적용되어 있고, 입력한 padding 값과 합쳐져서 결국 box의 실제 크기는 width가 530px, height가 520px이 되어버렸다.  
이는 HTML에서 작성되는 모든 태그들은 box-sizing이 content-box이기 때문에 발생하는 문제이다.

box-sizing이란 어떤 속성일까?  
content-box를 속성값으로 사용하면 코드로 입력한 width, height 값이 content 영역의 넓이, 높이가 된다.  
border-box를 속성값으로 사용하면 코드로 입력한 width, height 값이 border 영역까지 포함된 넓이, 높이가 된다.

위에서 내가 원하는대로 box 크기가 조절되지않았던 이유를 알게되었다.  
그러면 border-box를 적용해보자.  
CSS 코드를 아래와 같이 수정하겠다.

```css
.box {
  width: 480px;
  height: 480px;
  padding-top: 40px;
  padding-left: 50px;
  box-sizing: border-box;
}
```

결과는 어떻게 나올까? 개발자 도구로 살펴보자.

<img width="181" alt="스크린샷 2022-02-25 오후 7 22 55" src="https://user-images.githubusercontent.com/86224851/155698618-884c60a5-7f73-4c8a-828c-55ce12e05e77.png">

<img width="277" alt="스크린샷 2022-02-25 오후 7 23 19" src="https://user-images.githubusercontent.com/86224851/155698684-1dedd548-b6de-4a5c-82fc-1bf728b0f063.png">

모든 코드가 그대로인 상황에서 box-sizing 속성만 border-box 값으로 설정했다.  
content 부분의 width, height가 자동적으로 padding 값과 연산되어 480px이 되도록 조절된 것이 확인됐다.  
border 부분까지 포함된 width, height로 변경된 것이다!  
border까지 추가해보자.

```css
.box {
  width: 480px;
  height: 480px;
  padding-top: 40px;
  padding-left: 50px;
  box-sizing: border-box;
  border: 2px solid black;
}
```

<img width="186" alt="스크린샷 2022-02-25 오후 7 26 43" src="https://user-images.githubusercontent.com/86224851/155699228-f17096f0-dc18-4c2b-988d-d118685b9b33.png">

border, padding, content 부분을 모두 합쳐서 480px이 되도록 변경되었다.  
이렇게 **box-sizing: border-box;** 를 사용하면 훨씬 더 직관적이게 box를 만들 수 있다.  
따라서 많은 개발자들이 CSS를 시작할 때 아래 코드와 같이 전체 태그에 이를 적용하고 시작한다고 한다.

```css
* {
  box-sizing: border-box;
}
```

\* 표시는 모든 태그를 선택하는 전체 선택자이다.

## 🙋🏻 Display

모든 HTML 요소는 display 속성을 가지고 있다.  
**display** 속성은 box의 type을 결정해준다.
어떤 값이 어떤 기능을 가지고 있는지 지금부터 살펴보자.

## Block

block 값을 가장 잘 설명하는 것은 "길막"이다.  
이 값은 자신을 제외한 다른 요소가 자기와 같은 줄에 서는 것을 용납하지 않기 때문이다.
예시를 보면서 설명하겠다. 아래와 같은 HTML 코드가 있다.  
div 태그는 display 속성의 값이 block이다.

```html
<body>
  <div class="parent">
    <div class="child">child</div>
    <div class="other">other</div>
  </div>
</body>
```

구분하기 쉽게 색상을 추가했다.

<img width="885" alt="스크린샷 2022-02-25 오후 8 25 08" src="https://user-images.githubusercontent.com/86224851/155707370-e15f2865-20ea-4b59-9c16-5d6eaa843fc7.png">

div 태그 하나가 화면의 한 줄을 모두 차지하고 있는 것을 볼 수 있다.  
이는 block이 별도로 width 값을 지정하지않으면 자동적으로 "부모의 content-box의 100% = 자신의 width"를 선언하기 때문이다.  
그렇다면 width를 설정하면 어떨까?

```css
.child {
  width: 500px;
}

.other {
  width: 100px;
}
```

<img width="886" alt="스크린샷 2022-02-25 오후 8 29 10" src="https://user-images.githubusercontent.com/86224851/155707892-d3b4b955-9416-400f-88aa-8202da0b8843.png">

여전히 한 줄을 차지하고 있으며, 남은 공간을 자동으로 margin으로 처리한다.  
참고로 이렇게 생긴 margin은 개발자 도구에 보이지않으므로 이 속성의 특징을 잘 알아두자!
width에 대한 특징은 알았으니, height를 살펴보자.

<img width="885" alt="스크린샷 2022-02-25 오후 8 34 20" src="https://user-images.githubusercontent.com/86224851/155708533-cb977147-61c1-4cd8-9866-5ade03f9b0b5.png">

현재 별도로 height 값을 지정하지않았는데, 부모 요소인 div.parent의 높이가 두 div의 합과 같다는 것을 알 수 있다.  
즉, 부모 요소의 height를 별도로 선언하지 않으면, "자식 요소의 height 합 = 부모 요소의 height"가 된다는 것이다.  
만약, margin을 설정해도 그만큼 height 값이 커진다.

```css
.child {
  width: 500px;
  height: 50px;
  margin-bottom: 50px;
}

.other {
  width: 100px;
  height: 50px;
}
```

<img width="884" alt="스크린샷 2022-02-25 오후 8 41 42" src="https://user-images.githubusercontent.com/86224851/155709415-349cffe3-8960-4a5b-8603-4c00204d042d.png">

두 자식 div의 height와 margin 값이 합쳐진 것이 div.parent의 height가 된 것을 확인할 수 있다.

앞서, block은 본인의 넓이로 채워지지않는 부분을 자동으로 margin으로 채운다고 했었다.  
이 것을 활용하여 요소의 정렬을 할 수 있다.

```css
.child {
  width: 500px;
  height: 50px;
  margin-bottom: 50px;
  margin-left: auto;
}
```

**margin-left: auto;** 를 사용하면 오른쪽에 자동으로 생성된 margin을 왼쪽으로 몰빵하게 된다.  
결과를 보면 쉽게 이해할 수 있다.

<img width="886" alt="스크린샷 2022-02-25 오후 8 49 47" src="https://user-images.githubusercontent.com/86224851/155710466-778c0127-7a1c-483e-8dff-9e318288f2dc.png">

반대로 **margin-left: auto;** 를 사용하면 왼쪽에 자동으로 생성된 margin을 오른쪽으로 몰빵하게 된다.  
사실 이건, 기본적으로 block이 가지고있는 특성이라 자동으로 적용되고 있다고 생각하자.  
결과는 아래와 같다.

<img width="885" alt="스크린샷 2022-02-25 오후 8 57 58" src="https://user-images.githubusercontent.com/86224851/155711470-796699d0-c0ec-4ed3-a0cc-ea7366d242a6.png">

그럼 만약 margin-left, margin-right를 동시에 사용하면 어떻게 될까?
두 개를 동시에 auto로 설정하면 속기법을 이용한 margin으로 표현할 수 있을 것이다.  
그렇다면 아래와 같은 코드가 될 것이다.

```css
.child {
  width: 500px;
  height: 50px;
  margin-bottom: 50px;
  margin: 0 auto;
}
```

자동 생성된 margin을 좌우에 똑같이 배분한 것이다.  
그 결과 가운데 정렬이 된 것을 확인할 수 있다.

<img width="885" alt="스크린샷 2022-02-25 오후 8 59 16" src="https://user-images.githubusercontent.com/86224851/155711645-4cfc586d-2cda-4624-bd74-512ff3216f09.png">

## Inline

inline을 가장 잘 설명하는 단어는 "흐름"이다.  
block과는 다르게 옆으로 주르륵 늘어서서 흐르려는 성질을 가지고 있다.  
워드같은 곳에 글 쓰는 것과 같다고 생각하면 이해가 쉽다.  
아래 사진을 보면, p 태그를 사용해서 텍스트를 작성하면 공간이 허용하는 곳까지 계속 이어지는 것을 볼 수 있다.  
또한 span 태그를 사용해 특정 텍스트를 꾸미는 것도 inline 속성이므로 기존 텍스트에 전혀 영향을 주지않는다.  
<img width="885" alt="스크린샷 2022-02-28 오전 10 02 07" src="https://user-images.githubusercontent.com/86224851/155908372-b2a90b9f-3923-46d4-850a-63d243dc2510.png">

그런데 만약 주르륵 나열되고, 공간이 넘어가면 줄이 바뀌면서 또 다시 나열되는 이 속성에 흐름을 방해하는 요소가 나타나면 어떻게 될까?  
옆으로 나열되는 것들을 방해하려면...위,아래로 뭔가 공간을 침범하는 것을 적용해보자!
span으로 꾸며줬던 텍스트에 padding-bottom을 줘서 아래쪽 텍스트에 대한 영향을 살펴보겠다.

```css
span {
  color: #fff;
  background-color: #0066ff;
  padding-bottom: 60px;
}
```

<img width="884" alt="스크린샷 2022-02-28 오전 10 07 49" src="https://user-images.githubusercontent.com/86224851/155908653-04cd2eb8-d650-4dbe-a3df-440fca7192b7.png">
아래쪽 텍스트를 덮어버렸지만, 텍스트들이 전혀 신경 쓰지 않고 진행되는 것을 볼 수 있다.

즉, 공간으로 인식하지 않고 있다는 것이다!  
그렇다면 margin-bottom을 입력해보자.

```css
span {
  color: #fff;
  background-color: #0066ff;
  padding-bottom: 60px;
  margin-bottom: 100px;
}
```

<img width="885" alt="스크린샷 2022-02-28 오전 10 13 00" src="https://user-images.githubusercontent.com/86224851/155908975-aa8b7d2c-166f-4f2a-85a5-57357c06e58c.png">

분명히 값을 정확히 입력이 됐는데, 개발자 도구를 통해 살펴보니 실체를 가지고 있지않는 것이 확인된다.  
이를 통해, 상하 방향으로 변경되는 것들은 inline 속성을 가진 것들에게 전혀 영향을 주지 못하거나 제 기능을 발현하지 못하는 것을 확인 할 수 있었다.  
따라서, inline 속성을 가지고 있는 요소들은 width, height, padding-top, padding-bottom, border-top, border-bottom, margin-top, margin-bottom 속성을 사용할 수 없다.  
물론 left, right 방향은 흐름을 방해하지 않고 따라가는 방향이므로 적용 가능하다!!

```css
span {
  color: #fff;
  background-color: #0066ff;
  padding-left: 40px;
  padding-right: 100px;
  margin-right: 20px;
}
```

<img width="884" alt="스크린샷 2022-02-28 오전 10 20 12" src="https://user-images.githubusercontent.com/86224851/155909419-9ac1cbb6-ab76-4da9-b570-95fd783d7dee.png">
좌우 방향으로는 아무 문제없이 값이 적용된다.

## inline-block

inline-block은 짬짜면 같은 존재다.  
block과 inline의 좋은 점을 모아둔 것이다.  
이 속성을 사용하면 block처럼 영역을 활용하면서 inline처럼 흐르게 할 수 있다.

```css
span {
  color: white;
  background-color: #0066ff;
  display: inline-block;
  width: 700px;
  height: 300px;
  padding-top: 30px;
  margin-bottom: 20px;
}
```

<img width="885" alt="스크린샷 2022-02-28 오전 10 26 26" src="https://user-images.githubusercontent.com/86224851/155909798-5721eed8-349d-4699-95d4-789a0bfaff46.png">

inline-block으로 설정된 span 태그가 block에서 사용 가능한 속성들을 제대로 반영하면서 다른 텍스트에 영향을 주면서도, inline으로 흐름을 따라가고 있는 것을 확인 할 수 있다.
