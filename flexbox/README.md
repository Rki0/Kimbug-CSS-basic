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
  align-items: flex-end;
  align-content: center;
  flex-wrap: wrap;
  width: 600px;
  height: 1000px;
  margin: 0 auto;
  background-color: #eff2f7;
}
```

3개의 .child를 flexbox로 활용하기 위해 부모 요소인 .parent에 **dispaly:flex;** 를 입력했다.  
flex-direction이 row이므로 가로축이 main axis이며 방향은 왼쪽에서 오른쪽이다.  
이렇게하면
