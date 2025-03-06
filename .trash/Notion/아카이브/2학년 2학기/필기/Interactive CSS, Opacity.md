---
강의 리스트:
  - "[[웹어플리케이션개발]]"
생성 일시: 2024-03-28
유형: 필기
주차:
  - 4주차
---
> [!important] Opacity 와 RGBA의 차이점
> 
>   
> Hover 와 Transition을 통한 CSS Interaction 을 공부했다.  

## HTML

```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>CSS Interaction</title>
        <meta charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="style.css">



    </head>

    <body>
        <h2>Opacity</h2>
        <h3>Opacity vs RGBA</h3>

        <div class="bg">
            <div class="opacity">
                <h3>Opacity</h3>
                    <!-- 헤더 태그는 각자 고유한 마진이 존재함 -->
                <p>Opacity는 자식 엘레먼트까지 다 투명도가 적용이 됩니다.</p>


            </div>
        </div>

        <div class="bg">
            <div class="rgba">
                <h3>Opacity</h3>
                    <!-- 헤더 태그는 각자 고유한 마진이 존재함 -->
                <p>RGBA는 자식 엘레먼트에는 투명도가 적용 되지 않습니다.</p>
            </div>
        </div>

        <h3>Opacity Transition</h3>
        <img src="mario.png" class="opacity-transition">
            <!-- 마우스가 올라가면 롤-오버 / 호버, 내려오면 롤-다운 -->
        

        <h2>Transform</h2>
        <h3>Scale</h3>
        <div class="box"></div>

        <h3>Rotate</h3>
        <div class="box-rotate"></div>

        <h3>Translate X</h3>
        <div class="circle-alone"></div>
        <div class="container-x">
            <div class="circle"></div>
        </div>

        <h3>Translate Y</h3>
        <div class="container-y">
            <div class="circle"></div>
        </div>

        <h3>Translate</h3>
        <div class="container">
            <div class="square"></div>
        </div>


    </body>
</html>
```

  

## CSS

```CSS
.bg {
    background: url('mario.png');
        /* 배경은 공간이 있어야 표현됨, 자리가 남으면 반복됨-타일마냥 */
    border: 2px solid salmon;
    height: 256px;
    width: 256px;
}

.opacity {
    /* height: 100%; 해도 된다! */
    height: inherit;
    background-color: \#fff;
    opacity: 0.5;;
}

.rgba {
    height: inherit;
    background-color: rgba(255, 255, 255, 0.5);
}

/* bg 밑의 h3 들에 모두 적용되는 스타일 */
.bg h3 {
    margin-top: 0;
}


.opacity-transition {
    transition: all 0.5s
        /* 전환은 항상 대기상태여야 하므로 이 클라스에 선언 */
}

/* 마우스가 올라갔을때 적용되는 클라스 */
.opacity-transition:hover {
    opacity: 0;
}

.box {
    width: 100px;
    height: 100px;
    margin: 100px;
    background-color: salmon;
    transition: all 0.1s;
}

.box:hover {
    transform: scale(2);
        /* scaleX 하면 가로만 커지고 scaleY 하면 세로만 커짐 */
}

.box-rotate {
    width: 100px;
    height: 100px;
    margin: 100px;
    background-color: crimson;
    transition: all 3s;
}

.box-rotate:hover {
    transform: rotate(1080deg);
        /* rotateX하면 가로로 돔 ㄷㄷ;; */
}

.circle-alone {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: blue;
    transition: all 2s;
}

.circle-alone:hover {
    transform: translateX(500px);
}


.container-x {
    width: 50px;
    border: 2px dashed orangered;
}

.circle {
    width: 50px;
    height: 50px;
    border-radius: 50%;
    background-color: green;
    transition: all 2s;
}

.container-x:hover .circle {
    /* container-x 에 마우스가 올라가면 circle을 움직인다! */
    transform: translateX(500px);
        /* 반대로 움직이고 싶으면 - 붙인다! */
}

.container-y {
    width: 50px;
    border: 2px dashed brown;
}

.container-y:hover .circle {
    /* 호버가 부모 클래스에 적용되기 때문에 자식인 circle도 호버가 적용됨 */
    transform: translateY(-500px);
}

.container {
    width: 150px;
    border: 2px dotted purple;
    margin: 200px;
}

.square {
    width: 150px;
    height: 150px;
    background-color: aqua;
    transition: all 2s;
}

.container:hover .square {
    transform: translate(200px, 200px);
}
```