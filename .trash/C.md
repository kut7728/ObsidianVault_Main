
# 문법

  

- `[this.name](http://this.name)` : 현재 스크립트가 돌아가는 객체의 이름을 출력
- `Debug.Log()` : print함수 마냥 콘솔에 값 출력
- `Input.GetKeyDown()` : 인자로 받는 키가 눌리면 참
- GameObject 라는 데이터 형이 존재함
    - `[GameObject 변수이름].transform.position.y` → 겜옵의 위치 좌표중 y축 값 출력

  

## 변수 선언

- float 데이터형으로 변수를 선언할때는 숫자뒤에 f `float weight = 81.2f;`

  

## 메소드 선언

- 메소드 생성 후 실행하려면 start나 update 브라켓에서 실행해줘야 함
- 메소드 생성하면서 인수를 줄때 데이터형도 표기
    
    ```C#
    void changeName(string something) {}
    ```
    
- 출력값이 있는 메소드는 앞에 데이터형 명시
    
    ```C#
    string fullName(string lastName) {
            string yourName = lastName + firstName;
            return yourName;
        }
    ```
    
      
    

## 배열 선언

```C#
GameObject[] objs;     // GameObject 리스트 데이터형인 objs 선언 

objs = new GameObject[3];     
// 크기 지정을 위해 재선언, 이때 동일한 이름 쓰려면 new를 붙여줘야함

int[] arrayInt = int[5];     // int 리스트인 arrayInt 를 크기 5로 선언
int[] ages = int[] {12,42,23,12,11};    // 리스트 초기화 방법
```

## 전역 변수와 지역 변수

- start 브라켓에서 변수 선언하면 update 브라켓에서는 참조 불가
- 변수 선언시 public 달면 unity에서 gui로 편집 가능

  

## for 반복문

```C#
for (int i=0; i <= 19; i++) {
	blablabla...
}
```

  

## foreach 반복문

```C#
foreach(GameObject go in gos) {
	Debug.Log(go.name);
}
```

- 겜옵 리스트인 gos를 하나씩 훑는 겜옵 go