---
과목:
  - HTML + CSS
  - JS
내용: JS 기초, JQuery
주차: 2주차
---
- 목차
    - [[#문법]]
        - [[#변수]]
        - [[#자료형]]
        - [[#함수]]
        - [[#조건문]]
        - [[#반복문]]
    - [[#JS 활용문법]]
        - [[#DOM]]
        - [[#JQuery]]

---

  

## 문법

HTML 파일에 `<script> </script>` 태그를 추가하고 작성

### 변수

- `let name = ‘bob’; console.log(name);`

### 자료형

- 리스트
    
    `let a = [’사과’, ‘배’, ‘수박’]; console.log(a[1]); → 배`
    
- 딕셔너리
    
    `let person = {’name’ : ‘bob’, ‘age’ : 30, ‘height’ = 180}; console.log(person[’name’]); → bob`
    

### 함수

```HTML
function hey() {
	alert('안녕하세요');
}
```

### 조건문

```HTML
let age = 18;
				
if (age < 20) {
	console.log('청소년입니다')
} else {
	console.log('성인입니다')
}

>>> 청소년입니다
```

### 반복문

```HTML
let ages = [15, 30, 29, 12, 11];

ages.forEach(a => {
	console.log(a)
});
```

  

## JS 활용문법

웹페이지에 상호작용을 추가하는 방법

~~JS를 적용하기 위해서는 태그를 ID 지정하는게 필수 인가봄~~

ID도 되고 Class 로도 가능, 다만 ID는 전체에서 하나만 지정가능함

### DOM

Document Object Model - 그냥 HTML 상에서 기본 JS 로 하는 걸 말하는 듯;;

```HTML
function hey() {
	alert('안녕!');
	document.getElementById('hello').style.color = 'red';
}
...
<button class="form-button" type="button" onclick="hey()">영화 기록하기</button>
```

- 영화 기록하기 버튼 누르면 `ID = ‘hello’` 가 지정된 문자의 색을 빨강으로 바꿔줌

  

### JQuery

DOM 보다 훨씬 쉽게 조작할 수 있게 해주는 라이브러리

- JQuery 임포트 하기
    - HTML의 head에 붙여넣어서 임포트 가능
        
        ```HTML
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>
        ```
        
- 예시 1
    
    ```HTML
    function hey() {
    	alert('안녕!');
    	$('\#title').text('쥬라기 월드')
    }
    ...
    <button class="form-button" type="button" onclick="hey()">영화 기록하기</button>
    ```
    
    - 영화 기록하기 버튼 누르면 `ID = ‘title’` 가 지정된 문자를 쥬라기 월드로 바꿔줌
    
      
    
- 예시 2
    
    ```HTML
    <script>
        function checkResult() {
            let fruits = ['사과','배','감','귤','수박'];
            $('\#q1').empty();
    
            let a = fruits[0];
            let temp_html = `<p>${a}</p>`;
            $('\#q1').append(temp_html);
        }
    </script>
    ```
    
    - `id=’q1’` 붙은 객체를 `.empty()` 로 비우고 `temp_html` 을 붙인다.
    - html 코드는 백틱``(`)`` 으로 감싸고 그 속에 변수를 넣고 싶다면 `${}` 로 감싸서 넣는다
    
      
    
- 예시 3 - foreach 를 사용한 리스트 반복문
    
    ```HTML
    <script>
        function checkResult() {
            let fruits = ['사과', '배', '감', '귤', '수박'];
            $('\#q1').empty();
    
            fruits.forEach(a => {
                let temp_html = `<p>${a}</p>`;
                $('\#q1').append(temp_html);
            }); 
        }
    </script>
    ```
    
      
    
- 예시 4 - foreach 와 딕셔너리를 사용한 반복문
    
    ```HTML
    <script>
        function checkResult() {
            let people = [
            {'name':'서영','age':24},
            {'name':'현아','age':30},
            {'name':'영환','age':12},
            {'name':'서연','age':15},
            {'name':'지용','age':18},
            {'name':'예지','age':36}
        ]
            $('\#q2').empty();
    
            people.forEach(a => {
                let temp_html = `<p>${a['name']}는 ${a['age']}살 입니다.</p>`;
                $('\#q2').append(temp_html);
            }); 
        }
    </script>
    ```