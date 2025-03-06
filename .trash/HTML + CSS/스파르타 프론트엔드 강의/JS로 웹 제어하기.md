---
과목:
  - HTML + CSS
  - JS
내용: jQuery, fetch, toggle(), document_ready
주차: 3주차
---
## jQuerry 기능

### `.toggle()` 로 포스팅박스 토글하기

```HTML
<script>
	function openclose() {
		  $('\#postingbox').toggle();
	}
</script>
```

- 버튼 누르면 지정한 항목을 보이게 / 안보이게 설정 가능
- 원리 : CSS의 display 값이 none이 되면서 사라지게 됨

  

### 데이터 인풋으로 받아오기

```HTML
function makeCard() {
  let image = $('\#image').val();
  alert(image);
}
```

- `ID=’image’` 가 붙은 input 태그의 값을 받아옴

  

### `.append()` 로 카드 생성하기

```HTML
function makeCard() {
    let image = $('\#image').val();
    let title = $('\#title').val();
    let content = $('\#content').val();
    let date = $('\#date').val();

    let temp_html = 
    `<div class="col">
        <div class="card h-100">
            <img src="${image}"
                class="card-img-top" alt="..." />
            <div class="card-body">
                <h5 class="card-title">${title}</h5>
                <p class="card-text">${content}</p>
            </div>
            <div class="card-footer">
                <small class="text-body-secondary">${date}</small>
            </div>
        </div>
    </div>`;
    $('\#card').append(temp_html);
}
```

  

## fetch

서버에서 데이터 받아오기

> [!important] **GET 요청**
> 
>   
>   
> https://movie.daum.net/moviedb/main?movieId=68593  
>   
>   
> movie.daum.net - 서버의 위치  
> moviedb/main - 정보를 가져오고자 하는 창구  
> movieId=68593 - 가져오고자 하는 정보  

  

### 서울시 미세먼지 openAPI 에서 정보 받아오기

```HTML
<style type="text/css">
    div.question-box {
        margin: 10px 0 20px 0;
    }

    .bad {
        color: red;
    }
</style>

<script>
    function q1() {
        $('\#names-q1').empty();

        let url = 'http://spartacodingclub.shop/sparta_api/seoulair';
        fetch(url).then(res => res.json()).then(data => {
            let rows = data['RealtimeCityAir']['row'];

            rows.forEach(a => {
                let gu_name = a['MSRSTE_NM']
                let gu_mise = a['IDEX_MVL']

                if (a['IDEX_MVL'] <= 40) {
                    $('\#names-q1').append(`<li class='bad'>${gu_name} : ${gu_mise}</li>`);
                } else {
                    $('\#names-q1').append(`<li>${gu_name} : ${gu_mise}</li>`);
                }
            });
        })
    }
</script>
```

- url에서 정보를 받아와서 res에 넣고 res를 json으로 바꾼것을 data로 넣고 출력
- 미세먼지 수치가 40 이하인 경우에 글씨를 빨간색으로 출력

  

### 페이지 로딩이 완료될때 fetch 해서 기본값을 바꿔주는 코드

```HTML
<script>
		$(document).ready(function () {
		    let url = "http://spartacodingclub.shop/sparta_api/seoulair";
		    fetch(url).then(res => res.json()).then(data => {
		        let mise = data['RealtimeCityAir']['row'][0]['IDEX_NM']
		        
		        $('\#msg').text(mise)
		
		    })
		})
</script>
```

- 기존에 적혀 있던 문구를 `<span></span>` 태그로 감싸고 `ID=’msg’` 로 지정해서 페이지 로딩이 끝날 때 변수 `mise` 값으로 바꿈