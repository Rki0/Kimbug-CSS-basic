# 🎨 Typography

Typography는 텍스트를 예쁘게 디자인하는 것을 말한다.  
다양한 속성이 있으므로 예시와 함께 하나씩 살펴보자.

## font-size

font-size는 텍스트의 크기를 조절한다.  
px, em, rem를 단위로 사용하며, px를 주로 사용한다.  
px는 절대 단위(Absolute unit)로, 어딜가든 1px, 2px...은 똑같은 크기를 가진다.  
em, rem은 상대 단위(Relative unit)로, 어디에 사용되느냐에 따라 크기가 달라진다.

em = equal to capital M 으로 대문자 M의 크기를 기준으로 한다...잘 이해가 되지않는다.  
쉽게 말하자면, 적용되어 있는 폰트 사이즈를 1em으로 본다는 것이다.  
예시를 통해 알아보자.

```html
<div class="parent">
  <p>
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Omnis deleniti odio
    voluptates unde et voluptatum dignissimos, fuga illo dolorum id tempora
    assumenda, quibusdam ab nesciunt ullam nemo ipsam itaque porro?
  </p>
</div>
```

위 코드에 아래와 같은 스타일을 적용했다고 하자.

```css
.parent {
  font-size: 20px;
}

p {
  font-size: 3em;
}
```

p 태그는 .parent에 의해 20px이 적용되어 있는 상태이다.  
여기서 p 태그의 font-size를 별도로 3em으로 지정했다.  
이렇게 되면 p 태그의 font-size는 3\*20 = 60px이 된다.  
개발자 도구를 통해 확인해보자.

<img width="556" alt="스크린샷 2022-03-09 오후 3 22 46" src="https://user-images.githubusercontent.com/86224851/157384287-3be7748d-da98-4775-b937-4d056d08dc69.png">

즉, 1em이라는 것은 먼저 적용되어 있는 font-size의 크기를 의미한다.

rem = root em 으로 root는 html을 의미한다.  
즉, html에 적용된 font-size를 1rem으로 생각한다는 뜻이다.

```css
html {
  font-size: 20px;
}

p {
  font-size: 1.5rem;
}
```

html 태그의 font-size를 1rem으로 생각하므로 1rem = 20px이며, 1.5rem은 30px이 될 것이다.  
개발자 도구를 통해 확인해보자.

<img width="555" alt="스크린샷 2022-03-09 오후 3 26 08" src="https://user-images.githubusercontent.com/86224851/157384679-6d41518e-117d-4f63-9acb-abf4ad0c6056.png">

## line-height

line-height는 줄간격을 조절할 때 사용한다.  
px, em, rem을 단위로 사용하며, em을 주로 사용한다.  
적용된 폰트 사이즈에 대하여 얼만큼의 간격을 만들 것인지가 주 목적이기 때문이다.  
특이하게 line-height에서는 em 단위를 사용할 때는 단위 표시를 생략하고 적는 것이 관례라고 한다..물론 px, rem을 사용한다면 단위를 적어줘야한다!

```css
p {
  font-size: 20px;
  font-height: 1.5;
}
```

p 태그의 font-size가 20px이기 때문에 line-height: 1.5; 는 1.5em을 의미하며 값은 30px이 될 것이다.  
개발자 도구를 통해 확인해보자.

<img width="554" alt="스크린샷 2022-03-09 오후 3 38 21" src="https://user-images.githubusercontent.com/86224851/157386228-9497d224-b0f5-43fc-8048-7bf65752ccff.png">

line-height의 특이한 점은 하나 더 있다.  
값을 얼마를 넣던 관계없이 텍스트는 항상 중간 높이에 정렬되어 있다는 것이다.  
그래서 텍스트를 가운데 높이에 정렬할 때 사용하기도 한다.

## letter-spacing

letter-spacing은 텍스트 간 간격을 조절할 때 사용한다.  
px, em을 단위로 사용하며, em을 주로 사용한다.  
해당 텍스트에 비례해서 몇 퍼센트만큼 줄이고 늘릴 것인지가 주 목적이기 때문이다.  
또한 em 단위를 생략하는 것은 line-height에서만 가능한 것이니 주의하자!  
음수를 입력하면 간격이 줄어들고, 양수를 쓰면 간격이 늘어난다.  
예시를 통해 살펴보자.

```css
p {
  font-size: 20px;
  font-height: 1.5;
}
```

아무것도 적용하지 않은 상태는 아래와 같다.

<img width="883" alt="스크린샷 2022-03-09 오후 3 42 57" src="https://user-images.githubusercontent.com/86224851/157386763-73c10846-a837-425b-a2ea-c76a6c99cb65.png">

이번에는 음수를 입력해보겠다.

```css
p {
  font-size: 20px;
  font-height: 1.5;
  letter-spacing: -0.05em;
}
```

결과는 아래와 같다.  
텍스트 간 간격이 줄어든 것을 볼 수 있다.

<img width="884" alt="스크린샷 2022-03-09 오후 3 43 59" src="https://user-images.githubusercontent.com/86224851/157386911-5072d12f-809b-42a0-ad35-3ae36bc98359.png">

이번에는 양수를 입력해보겠다.

```css
p {
  font-size: 20px;
  font-height: 1.5;
  letter-spacing: 0.05em;
}
```

결과는 아래와 같다.  
텍스트 간 간격이 기본 상태보다 늘어난 것을 볼 수 있다.

<img width="884" alt="스크린샷 2022-03-09 오후 3 44 58" src="https://user-images.githubusercontent.com/86224851/157387054-a3db5978-7a98-4b20-b6f9-992a51fe5af4.png">

## font-family

font-family는 텍스트의 서체(폰트)를 지정할 때 사용한다.  
크게 3가지의 사용법이 있다.
첫번 째 방법은 아래와 같다.

```css
body {
  font-family: "Poppins";
}
```

이는 단순히 "Poppins"라는 폰트를 사용하라고 하는 것이다.

두번 째 방법은 아래와 같다.

```css
body {
  font-family: "Poppins", sans-serif;
}
```

이는 "Poppins"라는 폰트를 사용하고, 만약 그 폰트가 없다면 sans-serif 종류의 폰트 중 아무것이나 사용하라고 하는 것이다.

세번 째 방법은 아래와 같다.

```css
body {
  font-family: "Poppins", "Roboto", sans-serif;
}
```

이는 "Poppins"라는 폰트를 사용하고, 만약 그 폰트가 없다면 "Roboto"라는 폰트를 사용하고, 만약 두 개가 다 없으면 sans-serif 종류의 폰트 중 아무것이나 사용하라고 하는 것이다.

여기서 sans-serif는 텍스트의 스타일을 의미하는데, 굳이 말하자면 돋움, 고딕체 같은 느낌으로..굵기가 일정하며 매끄러운 글씨체를 의미한다.  
letter-spacing에서 사용된 폰트이기도 하다.  
다른 종류로는 serif가 있다.  
명조체 같은 느낌으로..글씨체가 약간 삐죽삐죽 나와 있다.

```css
body {
  font-family: serif;
}
```

위 코드는 내 컴퓨터에 있는 가장 기본적인 serif체를 사용하라는 것으로 결과는 아래와 같다.

<img width="882" alt="스크린샷 2022-03-09 오후 3 52 01" src="https://user-images.githubusercontent.com/86224851/157388066-b1bdee0c-9dcb-4388-b08c-6ca41f2ba1dd.png">

삐죽삐죽 나와있다는 것이 어떤 느낌인지 비교가 되었으리라 생각한다.

## font-weight

font-weight는 텍스트의 두께를 조절한다.  
100씩 커지는 숫자를 적어서 값을 표현한다.  
300은 Light, 400이 Regular, 700은 Bold, 900은 최고 두께를 의미한다.  
400과 700을 가장 많이 사용한다.

```css
p {
  font-weight: 400;
}
```

가장 기본적인 두께를 나타낸다. 그래서 위에서 본 예시들과 차이가 없다..

<img width="883" alt="스크린샷 2022-03-09 오후 3 54 45" src="https://user-images.githubusercontent.com/86224851/157388465-85d24c18-8d39-49fb-87a5-81a1ce8ef3d9.png">

700으로 값을 높여보겠다.

```css
p {
  font-weight: 700;
}
```

텍스트의 두께가 두꺼워진 것을 확인 할 수 있다.

<img width="883" alt="스크린샷 2022-03-09 오후 3 56 26" src="https://user-images.githubusercontent.com/86224851/157388692-c2165732-35e0-4725-a6bc-d24e5e87c010.png">

## color

color는 텍스트의 색상을 설정한다.  
사용하는 방식은 색상 이름, hex, rgb, rgba로 4가지가 있다.

색상 이름을 입력하는 것은 편하긴하나 이름과 색상을 정확히 연상하는 것이 쉽지않기 때문에 잘 사용하지 않는 듯 하다.

hex는 #0066ff 처럼 #에 6자리의 숫자와 알파벳을 섞어 사용한다. 16진수 표현이라서 hex라고 한다.

```css
p {
  color: #0066ff;
}
```

파란색의 hex 표현을 사용하여 텍스트 생상을 변경했다.

<img width="884" alt="스크린샷 2022-03-09 오후 4 00 57" src="https://user-images.githubusercontent.com/86224851/157389305-4882c6d4-fe45-4cdb-829a-8ddf168588ef.png">

rgb는 rgba와 비슷하므로 rgba로 설명하겠다.

```css
p {
  color: rgba(0, 102, 255, 0.5);
}
```

rgba는 숫자를 4개를 입력하는데, rgb는 숫자를 3개만 입력한다.  
마지막 숫자는 투명도를 의미하는데, rgb는 투명도 조절을 할 수 없고, rgba는 투명도 조절이 가능하다는 차이가 있겠다.  
투명도는 0 ~ 1값을 입력할 수 있고, 0은 완전한 투명, 1로 갈수록 완전 불투명(투명이 아닌 상태)가 된다.

<img width="881" alt="스크린샷 2022-03-09 오후 4 04 07" src="https://user-images.githubusercontent.com/86224851/157389735-f64547c2-5294-4489-abe8-987912f773d7.png">

앞 3개의 숫자는 파란색을 의미하며, 0.5의 투명도를 부여했기 때문에 바로 위 예시에서 봤던 색깔보다 투명해진 것을 확인 할 수 있다.

## text-align

text-align은 텍스트를 정렬할 때 사용한다.  
주로 left, right, center를 사용하며, 말그대로 왼쪽, 오른쪽, 가운데 정렬을 의미한다.  
기본적으로 텍스트는 left로 정렬된다.  
바로 예시를 보도록하자.

```css
p {
  text-align: right;
}
```

<img width="884" alt="스크린샷 2022-03-09 오후 4 21 37" src="https://user-images.githubusercontent.com/86224851/157392190-bde56c31-df64-4cae-b578-ea06c5bddafc.png">

텍스트가 전부 오른쪽 정렬이 된 것을 볼 수 있다.  
이번에는 가운데 정렬을 해보자.

```css
p {
  text-align: center;
}
```

<img width="884" alt="스크린샷 2022-03-09 오후 4 22 35" src="https://user-images.githubusercontent.com/86224851/157392327-d1445cbf-86d8-4b41-a656-bf82b3df2552.png">

텍스트가 전부 가운데로 정렬된 것을 볼 수 있다.

## text-indent

text-indent는 들여쓰기를 설정할 때 사용한다.  
아래는 아무 설정도하지 않은 기본 텍스트이다.

<img width="880" alt="스크린샷 2022-03-09 오후 4 24 50" src="https://user-images.githubusercontent.com/86224851/157392651-95dfa881-f255-4ef3-b403-9e863f0dc986.png">

여기에 100px의 들여쓰기를 적용하겠다.

```css
p {
  text-indent: 100px;
}
```

<img width="878" alt="스크린샷 2022-03-09 오후 4 26 19" src="https://user-images.githubusercontent.com/86224851/157392883-4cc1f443-4069-490d-b98b-5219c486c364.png">

가장 윗 줄이 100px만큼 들여써진 것을 확인 할 수 있다.  
그런데 <br / > 태그를 사용해서 줄 띄움을 해준 곳에는 변화가 없었다.  
즉, 태그 하나의 첫 줄에만 적용이 된다는 것을 알 수 있다.  
또한 음수를 쓰면 앞쪽으로 들여쓰기가 된다.

```css
p {
  text-indent: -100px;
}
```

맨 윗 줄이 앞쪽으로 들여쓰기가 적용되어서 화면 밖으로 나가버렸다.

<img width="882" alt="스크린샷 2022-03-09 오후 4 28 13" src="https://user-images.githubusercontent.com/86224851/157393154-8ff75920-fa91-4292-87d9-27935563964d.png">

## text-transform

text-transform은 텍스트를 변형시킬 때 사용한다.  
이 속성은 영어 알파벳을 사용하는 텍스트에 유효하다.  
소문자에서 대문자, 대문자에서 소문자 등을 조절하는데 쓰인다.  
none, capitalize, uppercase, lowercase를 값으로 사용한다.  
none은 입력한 그대로를 유지하며, capitalize는 띄어쓰기가 될 때마다 텍스트의 시작을 대문자로 변경하며, uppercase는 모든 텍스트를 대문자로 변경하고, lowercase는 모든 텍스트를 소문자로 변경한다.  
너무나도 뻔한 기능이므로 하나의 예시만 살펴보자.

```css
p {
  text-transform: uppercase;
}
```

모든 텍스트가 대문자로 변경된 것을 확인할 수 있다.

<img width="882" alt="스크린샷 2022-03-09 오후 4 32 46" src="https://user-images.githubusercontent.com/86224851/157393793-332bfc7a-c126-4ee8-ba5a-37adce32a8f5.png">

## text-decoration

text-decoration은 텍스트에 줄을 긋는 것과 관련된 속성이다.  
none, underline, line-through, overline 값이 있다.  
none은 아무 것도 없는 상태이며, underline은 밑줄, line-through는 텍스트 가운데를 관통하는 취소선, overline은 윗줄을 만들어낸다.

```css
p {
  text-decoration: overline;
}
```

텍스트에 윗줄이 생긴 것을 확인할 수 있다.

<img width="879" alt="스크린샷 2022-03-09 오후 4 35 40" src="https://user-images.githubusercontent.com/86224851/157394198-655316de-8ac4-49b9-acc5-049179531ebf.png">

이번에는 취소선을 살펴보자.

```css
p {
  text-decoration: line-through;
}
```

<img width="881" alt="스크린샷 2022-03-09 오후 4 36 47" src="https://user-images.githubusercontent.com/86224851/157394369-8809644a-65f4-49e4-8c01-55ecd69c01e9.png">

사실 이 속성은 텍스트를 꾸미기보다는 불필요하게 꾸며져있는 선을 없앨 때 많이 사용한다.  
예를들어, a 태그는 자동적으로 underline이 붙어있는데, 이를 none으로 지정해서 밑줄을 제거한다.

## font-style

font-style은 텍스트의 기울기를 만들어낸다.  
normal, italic, oblique가 값으로 사용된다.  
normal은 말그대로 기본 텍스트의 형태이다.  
italic과 oblique는 텍스트를 기울이는데 두 값의 차이를 못 느끼겠으므로 italic을 예시로 사용해보겠다.

```css
p {
  font-style: italic;
}
```

텍스트가 기울어진 것을 볼 수 있다.

<img width="886" alt="스크린샷 2022-03-09 오후 4 42 40" src="https://user-images.githubusercontent.com/86224851/157395254-082f2b97-e18f-40b4-a4b5-3b4db65a6477.png">

사실 이 속성도 텍스트를 꾸미기보다는 불필요하게 꾸며져있는 스타일을 제거할 때 사용한다.  
예를들어, em 태그는 자동적으로 italic이 적용되어 있는데, 이를 normal로 지정해서 기울기를 없앤다.

이렇게 텍스트에 적용되는 다양한 속성들을 살펴보았다.  
🥳 수고하셨습니다.

webfont 파일에는 폰트 사용에 관한 자세한 설명이 있으니 확인해주세요~  
typography-1 파일에는 실무에서 유용하게 쓰는 방식을 연습해 봤으니 참고해주세요~
