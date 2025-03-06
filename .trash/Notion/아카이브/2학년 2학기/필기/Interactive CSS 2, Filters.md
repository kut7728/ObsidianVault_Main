---
강의 리스트:
  - "[[웹어플리케이션개발]]"
생성 일시: 2024-04-04
유형: 필기
주차:
  - 5주차
---
> [!important] CSS의 Filter 와 hover 를 통한 Interaction을 배웠다

### HTML

```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>CSS Interaction 2</title>
        <meta charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="style.css">

    </head>

    <body>

        <h1>CSS Interaction 2</h1>
        <h3>CSS Multiple Properties</h3>
        <div class="multi-property"></div>

        <h3>CSS Opacity</h3>
        <div class="css-opacity">

            <div class="img-container">
                <img src="images/img_01.jpg">
                <!-- <img src="images/img_02.png"> -->
                    <!-- 컨테이너가 없어도 두 사진은 겹치지 않게 배치됨
                    하지만 밑의 컨테이너와 두번째 사진은 겹쳐짐 ㄷㄷ -->
            </div>

            <div class="img-container">
                <img src="images/img_02.png">
            </div>

        </div>
        
        <h3>CSS Filter Drop-Shadow</h3>
        <div class="css-dropshadow">

            <div class="img-container-shadow">
                <img src="images/img_01.jpg">
                <!-- <img src="images/img_02.png"> -->
                    
            </div>

            <div class="img-container-shadow">
                <img src="images/img_02.png">
            </div>

        </div>
        
        <h3>CSS Filter Blur</h3>
        <div class="css-blur">
            <div class="img-container-blur">
                <img src="images/img_01.jpg">     
            </div>

            <div class="img-container-blur">
                <img src="images/img_02.png">
                <h1>Blurry Text</h1>
            </div>
        </div>
        
        <div>
            <h3>Span and <span class="space">&nbsp;&nbsp;&nbsp;&nbsp;</span> inline-flex</h3>
        </div>

        <p class="poem">
            죽는 날까지 하늘을 우러러<br>
            한점 부끄럼이 없기를,<br>
            잎새에 이는 바람에도<br>
            나는 괴로워했다.<br>
        </p>

        <h3>CSS Filters</h3>
        <div class="css-filters">
            <div class="img-container-filters">
                <img src="images/img_01.jpg">     
            </div>

            <div class="img-container-filters">
                <img src="images/img_02.png">
            </div>
        </div>
        
        
        <h3>CSS Complex</h3>
        <div class="css-complex">
            <div class="img-container-complex">
                <img src="images/img_01.jpg">     
            </div>

            <div class="img-container-complex">
                <img src="images/img_02.png">
            </div>
        </div>


    </body>
</html>
```

### CSS

```CSS
.multi-property {
    width: 100px;
    height: 100px;
    background-color: salmon;
    transition: width 2s, height 1s, transform 3s;
}

.multi-property:hover {
    /* transform: scale(2); */
        /* scale 은 중점이 물체의 중심이고, 늘어나도 다른 물체를 움직이지 않는다 */

    width: 200px;
    height: 200px;
        /* 중점이 좌상단이고, 늘어날때 다른 물체를 밀어버림 */

    transform: rotate(180deg);
}


.img-container {
    width: 128px;
    height: 128px;
    background-color: violet;
        /* 컨테이너가 사진보다 작아도 사진은 원래크기대로 나옴
        컨테이너가 작아지니 사진이 겹쳐짐 */
        
}


.img-container-shadow {
    width: 128px;
    height: 128px;
    background-color: mediumaquamarine;
        /* 컨테이너가 사진보다 작아도 사진은 원래크기대로 나옴
        컨테이너가 작아지니 사진이 겹쳐짐 */
        
    }
    
.img-container-shadow img {
    transition: filter 1s;

}

.img-container-shadow:hover img {
    filter: drop-shadow(8px 8px 10px crimson);
        /* png의 경우에는 픽셀이 있는 부분만 그림자 */
}




.img-container-blur {
    width: 128px;
    height: 256px;
    background-color: turquoise;
        /* 컨테이너가 사진보다 작아도 사진은 원래크기대로 나옴
        컨테이너가 작아지니 사진이 겹쳐짐 */
}
    
.img-container-blur img {
    transition: filter 1s;
}
.img-container-blur h1 {
    transition: filter 1s;
}

.img-container-blur:hover img {
    filter: blur(10px);
}
.img-container-blur:hover h1 {
    filter: blur(10px);
}



.poem {
    line-height: 50px;
        /* 행간 늘이기 */
    letter-spacing: 20px;
        /* 자간 늘이기 */
}


.img-container-filters {
    width: 128px;
    height: 128px;
}
    
.img-container-filters img {
    transition: filter 1s;
}

.img-container-filters:hover img {
    filter: blur(10px) drop-shadow(8px 8px 4px deeppink);
        /* 필터 여러개를 사용하면 트랜지션 시간 따로 지정은 안됨 */
}

.space {
    display: inline-flex;
    width: 50px;
    transition: width 1s;
    border: 1px dashed red;
}

.space:hover {
    width: 200px;
}


.img-container-complex {
    width: 128px;
    height: 128px;
}
    
.img-container-complex img {
    width: 128px;
    height: 128px;
    transition: filter 1s, width 2s, height 0.5s, transform 5s;
}

.img-container-complex:hover img {
    width: 256px;
    height: 256px;
        /* width와 height는 변경할려면 지정이 되어 있어야 함!, 이미지 뿐만 아님 */
    filter: blur(10px) drop-shadow(8px 8px 4px deeppink);
        /* 필터 여러개를 사용하면 트랜지션 시간 따로 지정은 안됨 */
    transform: rotate(180deg) translateY(100px);
}
```