---
layout: post
title: CSS3 Background
categories: css
---

* TOC
{:toc}

Background 관련 속성은 해당 요소의 배경으로 이미지 또는 색상을 정의한다.

자세한 내용은 [CSS Background and Borders](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Background_and_Borders)를 참조한다.

# 1. Background Image 속성

[background-image](https://developer.mozilla.org/en-US/docs/Web/CSS/background-image)

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      background-image: url("img/dot.png");
    }
    </style>
</head>
<body>
  <h1>Hello World!</h1>
  <p>This page has an image as the background!</p>
</body>
</html>
```

# 2. Background Repeat 속성

[background-repeat](https://developer.mozilla.org/en-US/docs/Web/CSS/background-repeat)

설정된 이미지의 크기가 화면보다 작으면 자동으로 이미지가 반복 출력되어 화면을 채우게 된다. 이것은 `background-repeat` 속성의 기본값이 `repeat`이기 때문이다.

x축으로만 배경 이미지를 반복할 경우, `background-repeat` 속성값에 `repeat-x`, y축으로만 배경 이미지를 반복할 경우, `repeat-y`를 설정한다.

```css
body {
  background-image: url("img/dot.png");
  background-repeat: repeat-x;
}
```

반복 출력을 멈추고 싶은 경우, `background-repeat` 속성값에 `no-repeat`를 설정한다.

```css
body {
  background-image: url("img/dot.png");
  background-repeat: no-repeat;
}
```

background-image에 복수개의 이미지를 설정할 경우, 먼저 설정된 이미지가 전면에 출력된다.

```css
body {
  background-image: url("img/dot.png"), url("img/paper.gif");
  background-repeat: no-repeat, repeat;
}
```

# 3. Background Size 속성

[background-size](https://developer.mozilla.org/en-US/docs/Web/CSS/background-size)

배경 이미지의 크기를 조절하고 싶은 경우, `background-size` 속성을 사용한다.

속성값은 px, %, cover, contain 등을 사용한다.

배경이미지의 width, height를 모두 설정할 수 있다. 이때 첫번째 값은 width, 두번째 값은 height를 의미한다. 하나의 값만을 지정한 경우, 지정한 값은 width를 의미하게 되며 height는 auto로 지정된다.

**1. px값 지정**

배경이미지 크기가 지정된 px값 그대로 설정된다.

```css
.bg {
  background-size: 700px 500px;
}
```

**2. %값 지정**

배경이미지 크기가 지정된 %값에 비례하여 설정된다. 화면을 줄이거나 늘리면 배경이미지의 크기도 따라서 변경되어 찌그러지는 현상이 나타난다.

```css
.bg {
  background-size: 100% 100%;
}
```

**3. cover 지정**

배경이미지의 크기 비율을 유지한 상태에서 부모 요소의 width, height 중 큰값에 배경이미지를 맞춘다. 따라서 이미지의 일부가 보이지 않을 수 있다.

```css
.bg {
  background-size: cover;
}
```

<p data-height="412" data-theme-id="0" data-slug-hash="GjvGmR" data-default-tab="result" data-user="ungmo2" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/ungmo2/pen/GjvGmR/">background: cover - example</a> by Ungmo Lee (<a href="http://codepen.io/ungmo2">@ungmo2</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

**4. contain 지정**

배경이미지의 크기 비율을 유지한 상태에서 부모 요소의 영역에 배경이미지가 보이지 않는 부분없이 전체가 들어갈 수 있도록 이미지 스케일을 조정한다.

```css
.bg {
  background-size: contain;
}
```

<p data-height="265" data-theme-id="0" data-slug-hash="GjvGER" data-default-tab="result" data-user="ungmo2" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/ungmo2/pen/GjvGER/">background: contain - example  </a> by Ungmo Lee (<a href="http://codepen.io/ungmo2">@ungmo2</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

width, height의 속성값은 공백으로 구분하여야 한다. 속성값을 쉼표로 구분하면 다른 배경이미지의 너비를 지정하는 것으로 인식되기 때문에 주의가 필요하다.

```css
body {
  background-image: url("front.png"), url("back.png");
  background-repeat: no-repeat, no-repeat;
  background-size: 100%, 500px;
}
```

# 4. Background Attachment 속성

[background-attachment](https://developer.mozilla.org/en-US/docs/Web/CSS/background-attachmen)

화면을 스크롤하면 배경 이미지도 함께 스크롤된다. 화면이 스크롤되더라도 배경이미지는 스크롤되지 않고 고정되어 있게 하려면 `background-attachment` 속성에 `fixed` 키워드를 지정한다.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    *, *:after, *:before {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    html, body {
      width:100%;
      height:100%;
    }

    .bg-wrap {
      height: 100%;

      background-image: url("http://poiemaweb.com/img/bg/stock-photo-125979219.jpg");
      /* Create the parallax scrolling effect */
      background-attachment: fixed;
      background-size: cover;
      background-position: center center;
      background-repeat: no-repeat;

      overflow:auto;
    }

    #page-wrap {
      width: 400px;
      margin: 50px auto;
      padding: 30px;
      background: white;
      box-shadow: 0 0 20px black;
      /* size/line-height | family */
      font: 15px/2 Georgia, Serif;
    }
  </style>
</head>
<body>
  <div class="bg-wrap">
    <div id="page-wrap">
      <p>Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Vestibulum tortor quam, feugiat vitae, ultricies eget, tempor sit amet, ante. Donec eu libero sit amet quam egestas semper. Aenean ultricies mi vitae est.</p>
      <p>Mauris placerat eleifend leo. Quisque sit amet est et sapien ullamcorper pharetra. Vestibulum erat wisi, condimentum sed, commodo vitae, ornare sit amet, wisi. Aenean fermentum, elit eget tincidunt condimentum, eros ipsum rutrum orci, sagittis tempus acus enim ac dui. Donec non enim in turpis pulvinar facilisis. Ut felis. Praesent dapibus, neque id cursus faucibus, tortor neque egestas augue, eu vulputate magna eros eu erat. Aliquam erat volutpat. Nam dui mi, tincidunt quis, accumsan porttitor, facilisis luctus, metus</p>
    </div>
  </div>
</body>
</html>
```

<p data-height="425" data-theme-id="0" data-slug-hash="qaXYyx" data-default-tab="result" data-user="ungmo2" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/ungmo2/pen/qaXYyx/">background:attachment - example</a> by Ungmo Lee (<a href="http://codepen.io/ungmo2">@ungmo2</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

# 5. Background Position 속성

[background-position](https://developer.mozilla.org/en-US/docs/Web/CSS/background-position)

일반적으로 background-image는 좌상단부터 이미지를 출력한다. 이때 background-position 속성을 사용하면 이미지의 좌표를 지정 할 수 있다.

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    body {
      margin: 0;
    }
    div {
      background-image: url("img/dot.png");
      background-color: #FFEE99;
      background-repeat: no-repeat;
      width: 32vw;
      height: 200px;
      margin-bottom: 2vw;
      float: left;
    }
    div:not(:nth-of-type(3n-2)) {
      margin-left: 2vw;
    }
    .example1 {
      background-position: top;
    }
    .example2 {
      background-position: bottom;
    }
    .example3 {
      background-position: center;
    }
    .example4 {
      background-position: left;
    }
    .example5 {
      background-position: right;
    }
    .example6 {
      /* <percentage> values */
      background-position: 25% 75%;
    }
    .example7 {
      /* <length> values */
      background-position: 10px 20px;
    }
    .example8 {
      background-image: url("img/dot.png"), url("img/dot.png");
      background-position: 0px 0px, center;
    }
  </style>
</head>

<body>
  <div class="example1">top</div>
  <div class="example2">bottom</div>
  <div class="example3">center</div>
  <div class="example4">left</div>
  <div class="example5">right</div>
  <div class="example6">25% 75%</div>
  <div class="example7">10px 20px</div>
  <div class="example8">0px 0px, center</div>
</body>
</html>
```

<p data-height="711" data-theme-id="0" data-slug-hash="dpzKKB" data-default-tab="result" data-user="ungmo2" data-embed-version="2" class="codepen">See the Pen <a href="http://codepen.io/ungmo2/pen/dpzKKB/">background-position example</a> by Ungmo Lee (<a href="http://codepen.io/ungmo2">@ungmo2</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

# 6. Background Color 속성

[background-color](https://developer.mozilla.org/en-US/docs/Web/CSS/background-color)

```css
div {
  background-color: red;
  background-color: rgb(255,255,255);
}
```

# 7. Background Shorthand

[background](https://developer.mozilla.org/en-US/docs/Web/CSS/background)

Shorthand Syntax

```
// any order
background: color || image || repeat || attachment || position
```

```html
<!DOCTYPE html>
<html>
<head>
  <style>
    div {
      /*background: color || image || repeat || attachment || position*/
      background: #FFEE99 url("img/dot.png") no-repeat center;
      width: 50vw;
      height: 300px;
    }
  </style>
</head>
<body>
  <div></div>
</body>
</html>
```

# Reference

* [W3C CSS Document](https://www.w3.org/TR/CSS/)