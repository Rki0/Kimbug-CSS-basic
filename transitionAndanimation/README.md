# 💥 Transition & Animation

이번에는 요소에 동적인 변화(스르륵~)를 만들어내는 속성을 배워보자.  
transition과 animation이 있는데 두 속성을 헷갈리는 경우가 있다.

transition은 요소가 "A -> B" 이런식으로 완전히 전환이 되고, 클래스명을 추가한다던지, hover가 되어야한다던지 등등..무엇이든 이벤트적인게 발생해야 작동을 한다. 또한, 부여한 효과의 반복 등 고급 기능은 없다.

animation은 요소가 "A -> B -> C" 이런식으로 단계별로 전환을 설정할 수 있고, 이벤트적인게 없어도 독단적으로 효과 적용이 가능하다. 또한, 반복 등의 고급 기능을 사용할 수 있다.

다음 html 코드를 통해 자세하게 기능을 알아보자.

```html
<body>
  <div class="box">Hello box</div>
</body>
```

.box의 기본 설정은 다음과 같다.

```css
.box {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 300px;
  height: 300px;
  color: white;
  background-color: #0066ff;
}
```

## transition

transition 속성은 내가 변화를 주고자하는 요소에 입력해준다.

transition에는 property, duration, [timing-function], [delay] 값을 넣어줘야한다. [] 표시는 생략 가능하다는 의미이다.

property는 말그대로 전환하고자하는 css 속성을 의미한다.

duration은 transition에 기입한 효과가 얼만큼의 시간에 걸쳐 발생할 것인지를 의미한다.  
ms, s를 단위로 사용하며, 1s = 1000ms이다.

[timing-function]은 변화의 속도를 의미한다.  
ease-in, ease-out, ease-in-out, cubic-bezier() 등이 있다.  
ease-in은 처음에 천천히 바뀌다가 뒤로 갈수록 빨라지는 것이다.
ease-out은 처음에 빨리 바뀌다가 뒤로 갈수록 느려지는 것이다.  
위 두 값은 변화의 가속도가 브라우저 자체에 이미 설정되어있다.  
내가 직접 변화의 가속도를 조정하고자 할 때 사용하는 것이 cubic-bezier()이다.  
http://cubic-bezier.com 에서 시뮬레이션 가능하니 유용하게 사용하자.

[delay]는 transition을 몇 초 뒤에 시작할지를 의미한다.  
ms, s를 단위로 사용한다.

이제 transition 속성에 입력되는 값들의 의미를 살펴봤으니 예제를 통해 확인해보자.

```css
.box {
  transition: font-size 2500ms;
}

.box.active {
  font-size: 30px;
}
```

위 코드는 다음과 같은 의미를 가진다.  
font-size 속성에 변화를 적용할 것이며, 2.5초 동안 그 변화가 진행되도록 했다.  
그 변화는 요소에 .active를 추가하면서 발동될 것이며, font-size를 30px로 변화시킨다.  
결과를 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158015060-d72618bf-baf2-41ff-a23b-1ead2e6f3794.gif">

코드 해석과 동일한 효과가 나타난 것을 확인했다.  
다른 속성값도 사용해보자.

```css
.box {
  transition: background-color 2500ms cubic-bezier(0.07, 1.48, 0.86, -0.56) 1000ms;
}

.box.active {
  background-color: tomato;
}
```

이번에는 background-color 속성을 #0066ff에서 tomato로 변경하며, 2.5초간 실행되며, 변화 속도가 cubic-bezier()에 설정한 가속도에 따라 달라질 것이다.  
또한 이 transition은 1초간 대기 후 시작될 것이다.  
결과를 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158015450-3eda2e39-e0bc-4a9f-b1c5-73cb0e75ed50.gif">

코드 해석과 동일한 효과가 나타난 것을 확인했다.
그런데..다른 속성들도 효과를 주고싶을 때는 어떻게 해야할까?  
여러 속성을 한번에 개별적으로 설정해주고 싶다면 아래와 같은 방법을 사용한다.

```css
.box {
  transition: font-size 1000ms ease-out, background-color 2000ms cubic-bezier(0.07, 1.48, 0.86, -0.56);
}

.box.active {
  font-size: 30px;
  background-color: tomato;
}
```

매우 간단하다. 쉼표를 이용해서 추가해주면 된다.  
그리고 변경할 내용을 .active에 입력해주면 된다.  
결과를 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158015583-994284c3-868b-4ae9-bff0-ebcf9219b8c4.gif">

코드 해석과 동일한 결과가 나온 것을 확인 할 수 있다.  
만약, 모든 속성에 동일한 효과를 넣고 싶다면 property 부분에 all을 입력하면 된다.

```css
.box {
  transition: all 2500ms cubic-bezier(0.07, 1.48, 0.86, -0.56) 1000ms;
}

.box.active {
  font-size: 30px;
  background-color: tomato;
}
```

이러면 .active에 적용된 변경할 속성들이 같은 방식으로 변환이 진행된다.  
결과를 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158015858-f5e13b6d-8efb-47c2-8d48-b00d7ee5f573.gif">

변경이 적용되는 모든 속성이 같은 방식으로 변환되는 것을 확인했다.  
첫 부분에서도 언급했지만 transition 속성은 항상 어떠한 이벤트가 발생해야지만 발동이 된다.  
그래서 계속 .active를 작성하는 모습이 나왔던 것이다.

## animation

animation 속성 또한 효과를 주고자하는 요소에 작성해준다.

animation 속성에는 적용할 애니메이션 이름, duration, timing-function, delay, iteration-count, direction 값을 적어준다.  
속기법으로 한번에 작성할 수 있지만 여기서는 각각의 기능을 살펴보기 위해서 따로따로 볼 것이다.

적용할 애니메이션 이름에는 직접 작성해놓은 애니메이션 이름을 기입한다.  
애니메이션을 작성하는 방법은 다음과 같다.  
크게 두가지의 방법이 있다.

첫 째는 from과 to를 사용하는 것이다. 단어에서부터 알 수 있듯이 시작과 끝을 의미한다.  
저 공간에는 변화를 줄 속성에 대해서만 작성해주면 된다.

둘 째는 % 단위를 사용하는 것이다. 이는 애니메이션의 진행 정도를 나타내는 것이며 아래 코드에서는 0%(시작), 50% 진행되었을 때, 100%(끝)에 보여줄 상태를 각각 적어준다.  
이 방법이 첫번 째 방법보다 훨씬 디테일하게 설정할 수 있다.

```css
@keyframes animation-name {
  from {
  }

  to {
  }
}

@keyframes animation-name {
  0% {
  }

  50% {
  }

  100% {
  }
}
```

이렇게 지정한 애니메이션은 변화가 끝나면 다시 원래 상태로 돌아온다.  
또한, 애니메이션을 적용하는 요소에 디폴트 값(시작 상태)을 넣어놓지않으면 애니메이션이 끝나는 순간 변화를 줬던 속성들이 사라지므로 적용할 요소에 반드시 디폴트 값을 넣어놔야한다!

duration, timing-function, delay는 transition과 완벽하게 동일한 내용이므로 생략한다.

iteration-count는 애니메이션을 몇 번 되풀이, 반복할지를 의미한다.  
예를들어, 3이라고 입력하면 해당 애니메이션을 3회 반복한다.

direction은 애니메이션의 진행 방향을 지정한다.  
from, to도 이런 방향에 해당하며, 예를들어 reverse를 사용하면 to -> from으로 애니메이션이 진행된다.  
여기에 들어가는 값은 정말 다양하므로 mdn같은 사이트에서 필요할 때마다 찾아보자.

이제 animation 속성에 입력되는 값들의 의미를 살펴봤으니 예제를 통해 확인해보자.

```css
.box {
  position: relative;
  background-color: #0066ff;
  animation-name: move-box;
  animation-duration: 2000ms;
  animation-timing-function: ease-in-out;
  animation-delay: 1000ms;
  animation-iteration-count: 3;
  animation-direction: alternate;
}

@keyframes move-box {
  from {
    top: 0;
    background-color: #0066ff;
  }

  to {
    top: 200px;
    background-color: #ff4949;
  }
}
```

위 코드는 다음과 같은 의미를 가진다.  
move-box라는 이름을 가진 애니메이션을 .box에 적용할 것이며,  
2초동안 그 애니메이션을 실행하며, ease-in-out 형태로 변화 속도가 가속되며,  
이 애니메이션은 1초의 대기 후 실행되며, 3회 반복하고,  
from -> to -> from -> to로 실행된다.  
결과를 살펴보자.

<img src="https://user-images.githubusercontent.com/86224851/158017158-7483a528-8c59-4163-b35b-cee1bdbf5ae9.gif">

코드 설명대로 효과가 적용된 것을 확인 할 수 있다.

alternate에 대해 설명을 덧붙이자면 애니메이션은 원래 한번 동작을 끝내면 원래 있던 자리로 바로 돌아가버리는데(원래 자리에서 "뿅"하고 나타난다), 이를 자연스럽게 이어서 보여주기 위해서 역순으로 돌아가는 효과를 낸다.  
만약, 이 속성을 사용하지 않는다면 애니메이션이 한번 끝나면 원래 자리에서 뿅 나타나고, 다시 한번 실행하고 뿅 나타나고, 다시 한번 실행하고 뿅 하고 나타나면서 애니메이션이 종료된다.

이상으로 transition과 animation 기초에 대한 공부를 마치겠습니다.  
transtion 파일과 animation 파일에 어려운 예제도 꼭 참고해주세요~!  
수고하셨습니다~!
