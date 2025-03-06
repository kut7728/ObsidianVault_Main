---
설명: Stateless, Stateful Widget
상위 항목:
  - "[[스파르타코딩 강의]]"
---
- 목차
    - [[#Flutter Widget]]
        - [[#Stateless Widget]]
        - [[#Stateful Widget]]
        - [[#Navigation]]

## Flutter Widget

- 둘다 Class 로 존재, 사용하려면 상속받는 형태로 사용

### Stateless Widget

- 화면이 한번 그려진 후 바뀌지 않음 = build() 함수가 한번만 작동  
    ex) 이미지 띄워주는 화면, 이용약관 화면  
    
    ```Dart
    class MyApp extends StatelessWidget {
    	MyApp();       // 생성자
    	
    	@override
    	Widget build(BuildContext context) {
    		return Text("hello");
    	}
    }
    ```
    
    - build() 함수가 이미 StatelessWidget 클래스 속에 있기때문에 override 함
    
    ---
    
    - StatelessWidget 예시코드와 실행 순서
        
        ```Dart
        import 'package:flutter/material.dart';
        
        void main() {
          print("시작");
          runApp(const MyApp());
        }
        
        // StatelessWidget을 상속
        class MyApp extends StatelessWidget {
          // 생성자
          const MyApp({Key? key}) : super(key: key);
        
          // build 라는 이름의 메서드(함수) 실행
          @override
          Widget build(BuildContext context) {
            print("build 호출");
        
            return const MaterialApp(
              home: Scaffold(
                body: Center(
                  child: Text(
                    "hello Stateless Widget",
                    style: TextStyle(fontSize: 35),
                  ),
                ),
              ),
            );
          }
        }
        ```
        
        1. main() 함수에서 시작
            1. print() 함수와 MyApp() 함수 실행
        2. MyApp() 함수는 StatelessWidget 클래스를 상속
        3. 상속받은 클래스 속 build() 라는 메소드 실행
            1. print() 함수 실행
            2. MaterialApp 위젯 리턴
        4. MaterialApp 위젯
            
            > [!important] **MaterialApp 위젯으로 묶어주는 이유**
            > 
            >   
            > 안해주면 오류가 나는 경우가 있음  
            > MaterialApp 대신 CupertinoApp 위젯으로 묶어도 가능  
            
            1. Scaffold 로 앱의 모양 틀 잡아주고
            2. body의 가운데에 text위젯 출력

  

### Stateful Widget

- 화면의 내용이 변하는 위젯, 즉 새로고침이 필요한 위젯 = build() 함수가 여러번 동작해야함
- Stateless widget 과 달리 클래스가 두개로 구성
    
    ```Dart
    class MyApp extends StatefulWidget {
    	MyApp();       // 생성자
    	
    	@override
    	State<MyApp> createState() => _MyAppState();   // State 생성
    }
    
    class _MyAppState extends State<MyApp> {
    	@override
    	Widget build(BuildContext context) {
    		return Text("Hello");
    	}
    }
    ```
    
    - `State<MyApp>`은 `MyApp` 위젯의 상태(state)를 담당하는 클래스
    - `_MyAppState`은 상태 클래스
    
    ---
    
    - Stateful Widget 예시코드와 실행 순서
        
        ```Dart
        // ignore_for_file: prefer_const_constructors
        import 'package:flutter/material.dart';
        
        void main() {
          print("시작");
          runApp(const MyApp());
        }
        
        // StatefulWidget을 상속
        class MyApp extends StatefulWidget {
          // 생성자
          const MyApp({Key? key}) : super(key: key);
        
          @override
          State<MyApp> createState() => _MyAppState();
        }
        
        // MyApp의 상태(State)를 나타내는 클래스
        class _MyAppState extends State<MyApp> {
          int number = 1; // number가 1인 상태
        
          @override
          Widget build(BuildContext context) {
            print("build 호출");
        
            return MaterialApp(
              home: Scaffold(
                body: Center(
                  child: Text("$number", style: TextStyle(fontSize: 35)), // $:변수를 문자열에 넣는 방법 (template literal)
                ),
                floatingActionButton: FloatingActionButton(
                  child: Icon(Icons.add),
                  onPressed: () {
                    print("클릭");
        
                    // setState : 내부의 함수 실행 후 build 메서드(함수)를 다시 호출해서 화면 갱신
                    setState(() {
                      number += 1; // number를 1만큼 증가
                    });
                  },
                ),
              ),
            );
          }
        }
        ```
        
        1. main() 함수 실행
            1. print(), MyApp() 함수 실행
        2. MyApp() 함수
            1. Stateful Widget 상속
            2. createState() 함수 실행 → _MyAppState() 인스턴스 생성
        3. _MyAppState() 함수
            1. State<MyApp> 클라스 상속
            2. number 변수 정수 1로 초기화 및 생성
            3. build() 함수 실행
        4. build() 함수
            1. print(”build 호출”) 함수 실행
            2. MaterialApp() 생성
        5. 버튼 클릭시
            
            1. print(”클릭”) 실행
            2. number 변수 1 증가
            3. setState() 에 의해 build 함수 다시 호출
            
              
            

  

### Navigation

: Stateless, Stateful widget을 통해 구현된 화면간에 이동

- 각 화면을 `Route` 라고 부르고, 화면을 이동 시켜주는 것이 `Navigator`

  

- 다음 페이지 이동
    
    ```Dart
    Navigator.push(
      context,
      MaterialPageRoute(builder: (context) => SecondPage()), // 이동하려는 페이지
    );
    ```
    
    > [!important]
    > 
    > `button` 위젯의 `onPressed` 함수 부분에 넣는 식으로 구현
    
- 현재 화면 종료
    
    ```Dart
    Navigator.pop(context); // 종료
    ```