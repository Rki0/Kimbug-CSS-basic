# 🛫 float

float은 그 해괴한 사용법으로 인해 점점 사용을 줄여가고 있다고 한다.  
그럼에도 이를 배워야하는 것은 기존 코드의 디버그를 위함이기도 하고, 아직까지 사용하고 있기 떄문이기도 하다.

## float의 특성

시작하기 앞서, 이해하기 쉽게 float을 사용하면 요소가 공중으로 붕 떠오른다고 생각하자!

### 1. 집 나간 내 새끼, 찾을 길이 없네

자식 요소가 float을 사용하게 되면, 부모 요소는 자식 요소를 집 나간 자식으로 본다.  
즉, 부모 요소가 가지고 있던 크기에서 붕 떠올라버렸기 때문에 부모 요소의 height가 줄어든다.
아래 예시를 통해 알아보자.

```html
<body>
  <div class="parent">
    <div class="child red">Child</div>
    <div class="child yellow">Child</div>
    <div class="child blue">Child</div>
  </div>
</body>
```

<img width="436" alt="스크린샷 2022-03-01 오전 11 33 51" src="https://user-images.githubusercontent.com/86224851/156093658-136bdb8f-ceed-4dcf-834a-89db04932411.png">

여기서 .red에만 float를 적용해보겠다.

```css
.child {
  width: 200px;
  height: 200px;
  text-align: center;
  color: #fff;
}

.red {
  float: left;
}
```

자식 요소 .red에게만 float를 적용했다.  
.red는 공중으로 붕 떠오르게 될 것이고, 비어버린 .red의 공간에 .yellow가 진입할 것이다.  
그럼 당연하게도 .blue도 같이 올라오게 될 것이다.  
결과를 살펴보자.

<img width="421" alt="스크린샷 2022-03-01 오전 11 37 07" src="https://user-images.githubusercontent.com/86224851/156093914-61a3a53e-6738-4a92-8d61-f3be8bcf337b.png">

살짝 이해하기 힘들 수도 있다. .red의 투명도를 최대로 높혀서 가려진 .yellow를 찾아보자.
opacity는 투명도 조절 속성으로 1에서부터 0으로 갈 수록 투명해진다.

```css
.red {
  opacity: 0;
}
```

<img width="421" alt="스크린샷 2022-03-01 오전 11 38 24" src="https://user-images.githubusercontent.com/86224851/156094043-71a236ca-1cc3-4a94-b72a-871c6cc613fe.png">

.red 아래에 .yellow가 빈 공간을 채워 들어왔다는 것을 확인할 수 있다.
이 때, 재밌는 점은 부모 요소의 height 값이 변경된다는 것이다.

<img width="412" alt="스크린샷 2022-03-01 오전 11 42 13" src="https://user-images.githubusercontent.com/86224851/156094469-514e3245-5d67-43be-a3a5-81a3cdb311ad.png">

원래는 자식 요소 당 height가 200px이어서 총 600px이 .parent의 height였는데, .red에 float를 적용하고나니 height가 400px이 된 것이다.  
이를 통해 float을 적용한 자식 요소는 부모 요소에게서 그 크기가 산정되지 않게 된다는 것을 알았다.
예제에 있는 3개의 요소를 전부 float 시켜버리면 어떻게 될까?  
당연하게도 부모 요소의 height는 0이 된다.  
이는 레이아웃을 굉장히 이상하게 만들어버리는 원인이 된다..  
이를 해결하는 방법은 마지막에 살펴보도록 하자.

### 2. block으로 신분 상승

float을 설정하면 요소의 display 속성이 뭐든간에 block으로 상승된다.  
따라서 block으로 사용할 수 있는 다양한 속성을 활용 가능하다.  
그런데...block이 조금 이상하다..??

### 3. 길막을 못해 슬픈 block

그렇다..분명 block 속성을 가지게 되었지만, block의 기본 특징인 길막은 적용이 되지않는다!  
block은 width를 설정하지 않으면 부모 요소의 width를 사용하는 반면,  
float을 통해 얻은 block 성질은 width를 설정하지 않는다면 본인의 content 길이 만큼만 width를 가진다.  
예시를 통해 살펴보자.

<img width="160" alt="스크린샷 2022-03-01 오전 11 58 23" src="https://user-images.githubusercontent.com/86224851/156096389-b0853d21-30aa-46e0-885e-cdf52f87ac64.png">

위에서 작성한 CSS 코드에서 .child의 width만 제거한 상태이다.  
float이 적용된 자식 요소들이 부모 요소의 width가 400px로 지정되어있음에도 불구하고 본인의 content 길이만큼만 width를 가지는 것을 볼 수 있다.  
또한, 길막을 하지 않고 있는 것도 볼 수 있다!  
block이라면 자동으로 자신의 width를 제외한 부분은 margin으로 채워야함에도 불구하고, 여기서는 자동으로 margin을 채우는 일이 없었다!!  
즉, block의 특성을 완전 똑같이 사용하지는 않는다는 것을 알았다.

이를 활용해서 float이 적용된 요소들끼리 배치가 어떻게 바뀌는지 살펴보자.  
다시 자식 요소 .child에 width 값을 200px로 복구했다.  
.red에만 float이 적용되었을 때는 앞에서 살펴보았다.  
이번에는 .yellow에도 float을 적용하겠다.

```css
.yellow {
  float: left;
}
```

<img width="426" alt="스크린샷 2022-03-01 오후 8 41 15" src="https://user-images.githubusercontent.com/86224851/156162985-46d6a43f-28ec-4e10-8c95-c2b7599bb1ba.png">

.yellow가 .red 오른쪽에 붙은 것을 확인할 수 있다.  
최대한 쉽게 이 현상을 설명해 보겠다.  
먼저 붕 떠있던 .red 아래에 .yellow가 들어갔었는데, 그 상태에서 float이 되었으니 .red에 막혀 제대로 붕 뜰 수가 없었다(.red와 같은 높이로 뜰 수 없었다.).  
따라서 .red와 같은 높이로 붕 뜨기 위해서 오른쪽으로 이동해 간 것이다.  
물론 이 때, 부모 요소의 width가 자식 요소의 width 2개를 충분히 포함할 수 있는 크기였기 때문에 가능한 것이다.  
만약 부모 요소의 width가 자식 요소 2개의 width인 400px보다 작았다면 .yellow는 .red와 같은 높이의 오른쪽에 올 수 없게되고, 같은 높이의 아래쪽에 배치되었을 것이다.  
아까 살펴봤듯이 현재 .blue는 .red 밑에 깔려 있다는 것을 알 수 있다. 이번에는 .blue까지 float을 줘보자.

```css
.blue {
  float: left;
}
```

<img width="426" alt="스크린샷 2022-03-01 오후 8 48 45" src="https://user-images.githubusercontent.com/86224851/156163918-85d1f30e-065b-4542-8d74-6edbd68c6bc4.png">

모든 자식 요소가 float 상태가 되어 같은 높이로 올라왔고, 부모 요소의 width를 넘지않는 범위에서 차례대로 쌓여지는 것을 볼 수 있다.  
위에서도 말했지만, 모든 자식 요소가 float이 되어버렸으니 부모 요소의 height는 0이다.

### 4. float, 나만 볼 수 있어요.

바로 위에서 알아보았듯 float이 적용되면 요소가 붕 떠오른다.  
이 때문에 떠오르지않은 요소들은 비어버린 공간을 채우기 위해 움직임이 발생한다.  
그런데...모든 요소들이 움직이는 것은 아니다..!!  
텍스트나 이미지 같은 인라인 요소들은 float의 존재를 인식해서 그 요소들을 뚫고 지나가지 못한다.  
예시를 통해 살펴보자.

<img width="885" alt="스크린샷 2022-03-01 오후 9 02 46" src="https://user-images.githubusercontent.com/86224851/156165814-b8550676-e76e-4c0c-8ac5-e0272b9979fa.png">

float이 된 요소들이 있고, 그 빈 공간을 채우기 위해 올라온 검은색 배경의 div 요소가 보인다.  
그런데, div의 배경색은 float에 막히지않고 잘 공간을 차지했는데...텍스트는 float이 적용된 요소를 뚫고 지나가지 못하고 있는 것을 확인 할 수 있다.  
자..이제 float이라는 속성이 얼마나 레이아웃을 휘저어 놓는지 뼈저리게 느꼈으니, 그 해결법에 대하여 알아보자.

## float으로 발생되는 문제점을 해결하는 방법!

float으로 인해 야기되는 레이아웃 문제를 해결하는 방법을 알아보자.

### 1. 부모 요소에 overflow: hidden;

이 방법은 부모 요소가 height가 0이 되더라도, 다시 자신의 자식 요소를 찾아낼 수 있게 만들어준다.

```css
.parent {
  width: 400px;
  background-color: #eff2f7;
  overflow: hidden;
}
```

즉, 부모 요소가 실체가 있는 height로 다시 회복된다는 것이다. 결과를 살펴보자.

<img width="884" alt="스크린샷 2022-03-01 오후 9 12 37" src="https://user-images.githubusercontent.com/86224851/156167123-95cb2702-47d3-40c6-b43e-8f54d81c9236.png">

텍스트가 제대로 height를 인식하고 그 아래로 이동한 것을 확인 할 수 있다.  
또한, 개발자 도구를 통해 .parent를 살펴보면 아래와 같다.

<img width="178" alt="스크린샷 2022-03-01 오후 9 13 52" src="https://user-images.githubusercontent.com/86224851/156167253-ea5dc886-3a33-4b07-bdcf-9924055c181b.png">

height의 값이 0에서 자식 요소들의 합인 600px로 회복된 것을 확인 할 수 있다.

### 2. Clearfix(clear 속성 사용하기)

clear 속성은 float으로 인해 망가진 속성들을 고치기 위한 속성으로, 가장 정석적인 float 문제 해결 방법이다.
이 속성은 display가 block인 요소에만 사용할 수 있다.  
clear 속성의 기능은 이 속성을 사용하는 요소에게 "너 옆에 누가 float을 가지고 레이아웃에 변칙을 주는지 인식할 수 있게 해줄게." 라고 알려주는 것이다.  
예시를 통해 알아보자.

```css
.other {
  background-color: black;
  color: white;
  clear: left;
}
```

위에서 float 요소들로 인한 빈 공간을 채우기 위해 올라갔던 텍스트 요소가 float 요소들을 뚫고 지나가지 못했던 그 예제에서 텍스트 요소에 "clear: left"를 사용했다.  
그 결과는 아래와 같다.

<img width="885" alt="스크린샷 2022-03-01 오후 9 22 19" src="https://user-images.githubusercontent.com/86224851/156168338-42ec91b4-6c64-4de8-bdf2-1a804dcc4db4.png">

float 요소들로 인해 .parent의 height가 0임에도 불구하고 float 요소들이 존재한다는 것을 인식하고, 그 아래로 내려간 것을 확인 할 수 있다.  
쉽게 말하면 float의 영향을 받기 전, 원래 있던 자리로 돌아갔다는 것이다.  
즉, float의 영향을 받지 않았다는 것이다.

자...무슨 효과가 있는지는 알겠는데...  
이렇게 하면 뭐가 좋은걸까??  
부모 요소는 float된 자식 요소의 height 값이 없어지는데, 두번째 자식 요소가 clear 속성을 사용하면 두번째 자식 요소를 기준으로 height를 산정하고,  
float인 자식 요소가 있음에도 불구하고 부모 요소가 올바르게 height 값을 표시할 수 있게 되는 것이다!!

예시를 통해 살펴보자.  
이번에는 컬러 박스만 남겨놓고 보겠다.

```css
.red {
  background-color: red;
  float: left;
}

.yellow {
  background-color: yellow;
  clear: left;
}

.blue {
  background-color: blue;
  float: left;
}
```

<img width="422" alt="스크린샷 2022-03-01 오후 9 35 00" src="https://user-images.githubusercontent.com/86224851/156169966-9ad911a2-5082-4b41-aa6a-d118616bc0ee.png">

.red는 float이 되었다. 따라서 .yellow가 빈 공간을 채우기 위해 .red 아래로 들어가야하는데...  
들어가지 않고, 본인이 원래 있어야할 자리에 잘 있다!  
또한 .parent 또한 height가 .red 만큼 줄어들지 않고, 400px을 유지하고 있다.  
물론, .blue는 float이므로 포함되지않고 있다.

<img width="416" alt="스크린샷 2022-03-01 오후 9 38 42" src="https://user-images.githubusercontent.com/86224851/156170434-381fe14c-1668-4f13-ae15-76fceca22f08.png">

이런 기능을 가진 clear 속성은 left, right, both를 값으로 가질 수 있다.  
both의 경우는 float: left 와 float: right 둘 모두의 영향을 받지 않겠다는 것이다.

### 3. CSS에 Pseudo element(가상 요소) 생성하기

위에서 알아본 2개의 방법은 HTML 요소에 스타일을 적용해서 해결하는 것이라서 마크업 문서가 조금 더러워질 가능성이 있다.  
따라서 CSS에서 직접 수정하는 방식도 있다.  
바로 pseudo element를 생성해서 clear를 적용하는 것이다.  
이 가상 요소라는 것은 각 요소 당 2개씩 만들 수 있다.  
::before, ::after 가 그 2개이다.
이 둘은 요소 앞에 생성되느냐, 뒤에 생성되느냐의 차이이다.  
이들은 기본적으로 display 속성이 inline 값을 가진다.  
우선 가상 요소 예시를 살펴보자.

```css
.pseudo::before {
  content: "🥳";
  margin-right: 20px;
  font-size: 30px;
}

.pseudo::after {
  content: "";
  display: inline-block;
  width: 10px;
  height: 20px;
  background-color: pink;
}
```

가상 요소는 반드시 content 속성을 작성해야한다.  
content를 사용하지않더라도 반드시 써야한다!

<img width="381" alt="스크린샷 2022-03-01 오후 9 52 20" src="https://user-images.githubusercontent.com/86224851/156172264-a6288c73-9bcd-4a6a-94f0-9bbf2d36115b.png">

이렇게 HTML에 마크업을 하지않고 바로 CSS에서 마크업을 한 것과 같은 효과를 낼 수 있다!

그렇다면 이 것을 어떻게 float 문제를 해결하는데 사용할 수 있을까?

```css
.parent::after {
  content: "";
  display: block;
  clear: left;
}
```

부모 요소에 가상 요소를 설정하고 clear 속성을 사용했다.

<img width="423" alt="스크린샷 2022-03-01 오후 9 57 09" src="https://user-images.githubusercontent.com/86224851/156172945-57262094-cc80-4c7e-b789-bad9109d255c.png">

부모 요소가 height를 회복한 것을 확인 할 수 있다.  
이렇게 하면 굳이 HTML 요소를 마크업 해서 따로 만들지 않아도 간단하게 CSS에서 float 문제를 해결 할 수 있다.  
물론 지금은 요소 개수가 얼마 없어서 HTML 마크업을 통해 해결하는 것과의 차이점이 잘 안 보이지만, 요소가 많아지기 시작하면 충분히 확인할 수 있을 것이다.
