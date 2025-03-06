---
강의 리스트:
  - "[[웹어플리케이션개발]]"
생성 일시: 2024-04-25
유형: 필기
주차:
  - 6주차
  - 7주차
---
![[/Untitled 26.png|Untitled 26.png]]

### HTML

```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>Simple Page</title>
        <meta charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="style.css">
    </head>

    <body>
        <div class="frame">
            <nav>
                <!-- div와 역할은 똑같지만 웹 표준 코딩을 따르기 위해 사용 -->
                <h2>Title</h2>
                <ul>
                    <!-- unordered list - 순서가 중요치 않은 항목 태드 -->
                    <li class="menu1">iOS</li>
                    <li>Android</li>
                    <li>Switch</li>
                </ul>
            </nav>

            <section class="description">
                <!-- div 사용해도 무방! -->
                <h2>Description</h2>
                <p>Randez-Vous는 우주를 배경으로한 캐주얼 게임입니다. <br>
                    당신은 원인모를 사고로 우주선과 함께 우주를 떠돌게 되었습니다. 블랙홀에 빠졌을 수도 있습니다. <br>
                    무한한 우주에 퍼져있는 우주 정거장과 광물 스테이션에 도킹을 하면서 목적지를 찾아가세요. <br>
                    제한된 자원으로 우주를 떠돌면서 광물을 모으세요. 광물을 모으면 우주선을 업그레이드 할 수 있습니다.
                </p>
            </section>

            <main>
                <!-- main도 div랑 역할은 동일 -->
                <div class="ui id">
                    <img src="images/id.png">
                </div>

                <div class="ui fuel">
                    <div class="fuel-bg">
                        <img src="images/fuel_back.png">
                    </div>
                    <div class="fuel-bar">
                        <img src="images/fuel_bar.png">
                    </div>
                </div>
                
                <div class="ui mineral">
                    <div class="mineral-bg">
                        <img src="images/mineral_back.png">
                    </div>
                    <div class="mineral-bar">
                        <img src="images/mineral_bar.png">
                    </div>
                </div>

                <div class="ui btn-setting">
                    <img src="images/btn_setting.png">
                </div>
                
                <div class="ui btn-play">
                    <img src="images/btn_play.png">
                </div>

                <div class="ui minimap">
                    <img src="images/minimap.png">
                </div>

                <div class="ui satellite">
                    <img src="images/satellite.png">
                </div>

                <div class="ui spacecraft">
                    <img src="images/spacecraft.png">
                </div>

                <div class="ui asteroid">
                    <img src="images/asteroid.png">
                </div>

                <div class="ui msg">
                    <img src="images/msg.png">
                        <!-- img 태그 속 alt는 이미지를 못불러올때 출력할 대사 -->
                </div>

                <div class="ui label">
                    <img src="images/label.png">
                </div>

                <div class="ui spaceman-container">
                    <div class="spaceman">
                        <img src="images/spaceman.png">
                    </div>
                </div>

            </main>

            <footer>
                <p>소프트웨어 융합대학에서 만듬 2024.</p>
            </footer>
        </div>
    </body>
</html>
```

  

### CSS

```CSS
body {
    width: 1920px;
    height: 1080px;
    border: 2px solid lime;
    
    margin: 0;
    padding: 0;
    background-color: \#04070e;
    background-image: url('images/laika.png'), url('images/sputnik.png');
        /* 배경색과 배경이미지는 같이 사용 가능! */
    background-repeat: no-repeat, no-repeat;
        /* 배경이미지가 2개라서 no-repeat도 2개 적어야 함 */
    background-position: 5% 94%, 95% 10%;
}

.frame {
    width: 1600px;
    margin: 0 auto;
        /* auto는 좌우 여백을 동일하게 주라는 뜻 */
    border: 2px dotted red;
    color: white;
        /* color는 텍스트의 색상 의미 */
}

nav {
    margin-bottom: 40px;
        /* nav와 description 사이 공간 띄우기 */
}

nav h2 {
    display: inline-block;
    }

nav ul {
    display: inline-block;
    list-style: none;
    float: right;
        /* 시냇물에 띄운것 마냥 오른쪽으로 흘러서 붙게함 */
    padding-top: 8px;
        /* list와 title 높이 맞추기 위해 */
}

nav ul li {
    display: inline;
        /* inline은 보통 본문 내용에 사용
        inline-block 사용해도 무방, 위아래 여백이 약간 있는듯? */
    padding: 7px 30px;
        /* 경계선 안쪽 여백 주기, 위아래 좌우 순서 */
    transition: color 1s;
}

    .menu1:hover {
        color: crimson;
    }
    nav ul li:nth-child(2):hover {
            /* nav 속 ul 속 li 중 2번째 항목이라는 뜻 - class 안하고 지명 가능! */
        color: lime;
    }
    nav ul li:last-child:hover {
            /* nav 속 ul 속 li 중 마지막 항목 */
        color: violet;
    }

.description {
    margin-bottom: 80px;
}

.description h2 {
    padding:  10px 20px;
}

.description p {
    padding:  0 40px;
    font-size: 11pt;
        /* 기본은 보통 12pt */
    line-height: 18pt;
}

main {
    position: relative;
    height: 900px;
    background: url('images/bg.png');
        /* interaction 할거 없는애들은 그냥 배경으로 퉁침 */
}

.ui {
    cursor: pointer;
    position: absolute;
        /* 위치 일일히 정해줄것, 
        absolute하면 기준이 브라우저 좌상단이 되버림, 부모 태그에서 relative하면
        기준이 부모태그가 됨*/
    display: inline-block;
        /* 서로 겹치고 하려면 필요 */
    border: 1px dashed gray;
    background-color: rgba(176, 21, 44, 0.3);

}

.id {
    top: 43px;
    left: 54px;
}


.fuel {
    top: 108px;
    left: 54px;
}
.fuel:hover .fuel-bar {
    transform: scaleX(0.3);
        /* 좌우로 변형, 이동은 translate */
}
.fuel-bar {
    position: absolute;
        /* 이미 ui 클래스가 absolute 임으로 기준은 ui fuel 임 */
    top: 8px;
    left: 24px;
    transition: transform 1s;
    transform-origin: center left;
        /* 위아래 좌우 순서 */
}


.mineral {
    top: 159px;
    left: 54px;
}
.mineral:hover .mineral-bar {
    opacity: 1;
}
.mineral-bar {
    position: absolute;
    top: 9px;
    left: 28px;
    transition: opacity 1s;
    opacity: 0;
}


footer {
    height: 136px;
        /* 배경의 높이가 136 온전히 표현하려면 크기 맞춰야함 */
    background: url('images/footer-bg.png') no-repeat;
    background-position: center;
        /* 예는 좌우 위아래 순서 */
    text-align: center;
}

footer p {
    line-height: 136px;
        /* 텍스트 한 줄의 높이를 키워서 가운데 맞춰줌 */
    text-shadow: 1px 1px 0 black;
}

.btn-setting {
    top: 43px;
    right: 53px;
    opacity: 0.5;
    transition: opacity 0.5s;

}
.btn-setting:hover {
    opacity: 1;
}

.btn-play {
    top: 93px;
    right: 102px;
    opacity: 0.5;
    transition: opacity 0.5s;
}
.btn-play:hover {
    opacity: 1;
}

.minimap {
    bottom: 38px;
    right: 53px;
    transform: scale(0.5);
    transition: transform 0.5s;
    transform-origin: right bottom;
        /* transform은 기본원점이 중앙, 원점을 변경, 순서는 상관없음 */   
}
.minimap:hover {
    transform: scale(1);
}

.satellite {
    bottom: 38px;
    left: 54px;
    transition: transform 1s;
        /* 가감속 운동 없이 움직이려면 뒤에 linear 붙이면 됨 */
}
.satellite:hover {
    transform: rotate(1080deg);
}

.spacecraft {
    top: 388px;
    left: 763px;
        /* 화면이 고정이기 때문에 absolute로 좌표 찍는게 가장 배치가 쉬움! */
    transition: transform 1s;
}
.spacecraft:hover {
    transform: rotate(270deg);
}

.asteroid {
    top: 265px;
    left: 612px;
    transition: all 2s;

}
.asteroid:hover {
    transform: rotate(720deg);
    filter: invert();
}

.msg {
    top: 536px;
    left: 696px;
    opacity: 0.5;
    transition: all 1s;
        /* 따로 시간을 설정하고 싶다면 각각 적고 컴마(,)로 분리
            transition: opacity 0.5s, filter 10s */
}
.msg:hover {
    opacity: 1;
    filter: hue-rotate(180deg);
        /* hue는 색상이라는 뜻, 색상환에서 몇도 돌릴지 */
}

.label {
    top: 60px;
    left: 979px;
    transition: transform 0.5s;

}
.label:hover {
    transform: rotateX(360deg);
}

.spaceman-container {
    width: 28px;
        /* spaceman이 absolute가 되면서 컨텐츠를 잃었기 때문에 너비를 따로 지정해줘야함 */
    left: 1355px;
    height: 368px;

}
.spaceman {
    position: absolute;
        /* 원점은 부모의 포지션으로 됨 */
    bottom: 0px;
    transition: transform 1s;
}

.spaceman-container:hover .spaceman{
        /* 호버하는 객체와 움직일 객체가 다를때는 이렇게 작성 */
    transform: translateY(-570px);
}
```