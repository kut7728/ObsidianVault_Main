---
강의 리스트:
  - "[[웹어플리케이션개발]]"
생성 일시: 2024-03-21
유형: 필기
주차:
  - 3주차
---
## 뉴몰피즘 디자인

- 음영을 통한 입체감

  

```HTML
<!DOCTYPE html>
<html>
    <head>
        <title>Neumorphism CSS Style</title>
        <link rel="preconnect" href="https://fonts.googleapis.com">
        <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
        <link href="https://fonts.googleapis.com/css2?family=Strait&display=swap" rel="stylesheet">
        <link rel="stylesheet" type="text/css" href="style.css">
    </head>

    <body>
        <div class="frame">
            <h2>NEUMORPHISM<br> CSS STYLE STUDY</h2>
            <button type="button" disabled class="rect-btn left">Rect</button>
            <button type="button" disabled class="rect-long-btn right">Rect Convex</button>
            <button type="button" disabled class="circle-btn center">Circle</button>
            <button type="button" disabled class="flat-btn">Flat</button>
            <button type="button" disabled class="rounded-btn bottom">Input Text</button>
        </div>
    </body>

</html>
```

```CSS
html, body {
    margin: 0;
        /* 경계 밖의 여백 */
    padding: 0;
        /* 경계안쪽 컨텐츠 사이 여백 */
    height: 100%;
}

body {
    display: flex;
        /* body 하위 요소들을 정렬할때 쓰는 방식 */
    justify-content: center;
        /* 좌우 중앙 정렬 */
    align-items: center;
        /* 상하 중앙 정렬 */
    background-color: \#eaeaea;
}

/* .은 class 라는 뜻 */
.frame {
    position: relative;
            /* button들의 위치 기준을 frame으로 정해줌 */
    height: 90%;
      /* 높이는 상대값이  적용되지 않음 : body의 높이는 무한이라서 */
    width: 86%;
      /* %는 상대값, px는 절대값 */
    border-radius: 20px;
    background: linear-gradient(145deg,\#ececec, \#f2f2f2);
    box-shadow: 20px 20px 50px \#CCC, -20px -20px 50px \#FFF;
                /* 가로 세로 블러 그림자 색 */
}

.frame h2 {
    color: #555;
                /* 라인 종류 : 긴 점선 */
    padding: 20px 0 50px 30px;
            /* 경계 속 여백 */
            /* top, right, bottom, left 순서 */
    font-family: "Strait", sans-serif;
                            /* Strait 폰트를 쓰되 없으면 2안을 쓰시오 */
    font: 32px;
}

.rect-btn {
    width: 80px;
    height: 80px;
    border: none;
    border-radius: 15px;
    background: linear-gradient(145deg,\#E5E5E5, \#FFF);
    box-shadow: 8px 8px 16px \#CCC, -8px -8px 16px \#FFF;
}

.rect-long-btn {
    width: 170px;
    height: 80px;
    border: none;
    border-radius: 15px;
    background: linear-gradient(145deg, \#FFF, \#E5E5E5);
    box-shadow: 8px 8px 16px \#CCC, -8px -8px 16px \#FFF;
}

.circle-btn {
    width: 100px;
    height: 100px;
    border: none;
    border-radius: 50%;
    background: linear-gradient(145deg, \#E5E5E5, \#FFF);
    box-shadow: 8px 8px 16px \#CCC, -8px -8px 16px \#FFF;
}

.flat-btn {
    width: 90%;
    height: 45px;
    border: none;
    border-radius: 25px;
    background: \#F0F0F0;
    box-shadow: 8px 8px 16px \#CCC, -8px -8px 16px \#FFF;

    position: absolute;
    bottom: 125px;
    left: 50%;
    transform: translate(-50%);
}

.rounded-btn {
    width: 90%;
    height: 50px;
    border: none;
    border-radius: 25px;
    background: linear-gradient(145deg, \#EEE, \#F0F0F0);
    box-shadow: inset 3px 3px 8px \#CCC, inset -3px -3px 8px \#FFF;
                /* inset 경계 안쪽으로 그림자 넣겠다는 뜻 */
}

.left {
    position: absolute;
            /* 고정된 위치, 근데 기준이 body임 ㄷㄷ;; */
            /* frame css 에서 relative 한 덕분에 기준이 frame으로 바뀜 */
    left: 8%;
}

.right {
    position: absolute;
    right: 8%;
}

.center {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
        /* 현재위치에서 수치만큼 이동 */
}

.bottom {
    position: absolute;
    bottom: 50px;
    left: 50%;
    transform: translate(-50%);
}
```

  

## html & css

- 웹에서는 index.html 파일을 가장먼저 참조한다
- css의 첫파일은 style로 짓는 관례있음

  

- <head> 안에는 문서에 대한 설정이 들어가고
- <body> 안에 주소창 밑의 화면 내용, 기본적으로 마진(여백)이 있다
- <title> 크롬 탭에 보이는 이름
- <link rel="stylesheet" type="text/css" href="style.css">
    - rel : relate (연관있다는 의미) type : 해당 파일의 타입명시 href : 경로
- padding : 여백 내
- 주석
    - html은 <!— —>
    - css는 /* */

  

### 블록태그

- 블록태그의 너비는 상위 태그의 100% 이다
    - <div>의 너비는 <body>의 100% 임으로 화면 너비 전체, 높이는 내부 컨텐츠의 높이 만큼

## 이름 지어주기

- id : 문서 통틀어 하나만 사용가능
- class : 여러개에 사용가능

  

- 폰트는 웹폰트를 사용함
- relative 를 또 쓰고 싶다면 button 속에 div를 하나 만들고 button과 크기를 일치시키고 div에 relative를 넣기