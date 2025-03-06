---
설명: Widget, Scaffold()
상위 항목:
  - "[[스파르타코딩 강의]]"
---
## Widget

- flutter는 모든것이 위젯으로 구성되어 있음
- 위젯을 조합해서 화면을 그려냄
    
    - Cupertino - ios 스타일 위젯
    - Material - android 스타일 위젯
    - 더 많은 위젯 종류 알아보기
        
        > [!info] Widget catalog  
        > A catalog of some of Flutter's rich set of widgets.  
        > [https://docs.flutter.dev/development/ui/widgets](https://docs.flutter.dev/development/ui/widgets)  
        
        > [!info] Flutter Widget of the Week  
        > Fighting the good fight for Widget Awareness!  
        > [https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG](https://www.youtube.com/playlist?list=PLjxrf2q8roU23XGwz3Km7sQZFTdB996iG)  
        
    
      
    

### Scaffold()

: traditional한 모바일 앱의 틀 잡아줌

- appbar
    - leading, actions - appbar의 타이틀 앞뒤에 붙는 아이콘들

## 디렉토리 구조

- lib : 주로 코딩하게 될 폴더
- pubspec.yaml : 설정과 라이브러리 담기는 폴더

  

## 단축키

- 위젯 속에서 `option + esc` : 해당 위젯이 가질 수 있는 속성 전부 보여줌

  

![[c2228368-2e1f-4003-8173-3abf08f96c27.png]]

```Dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      home: Scaffold(
        // 가장 traditional 한 모바일 앱의 구조를 틀로 만들어줌
        appBar: AppBar(
            centerTitle: true,
            backgroundColor: Colors.blue,
            title: Text(
              "Hello Flutter",
              style: TextStyle(fontSize: 28, color: Colors.white),
            )),
        body: SingleChildScrollView(
          child: Padding(
            padding: const EdgeInsets.all(16.0),
            child: Column(
              children: [
                Padding(
                  padding: const EdgeInsets.all(32.0),
                  child: Image.network(
                    "https://i.ibb.co/nngK6j3/startup.png",
                    width: 81,
                  ),
                ),
                TextField(
                  decoration: InputDecoration(labelText: "이메일"),
                ),
                TextField(
                  obscureText: true, // 정보보호를 위한 블러처리
                  decoration: InputDecoration(labelText: "비밀번호"),
                ),
                Container(
                  width: double.infinity, //폭은 부모(칼럼) 크기 따라감, 부모의 폭 전체를 가진다는 뜻
                  margin: EdgeInsets.only(top: 24),
                  child: ElevatedButton(
                    //이놈은 width 속성이 없음! 부모의 크기를 따라감
                    //그래서 버튼을 컨테이너라는 부모로 감싸고 부모의 크기를 조정
                    onPressed: () {
                      print("로그인 버튼 클릭");
                    },
                    child: Text('로그인'),
                  ),
                )
              ],
            ),
          ),
        ),
      ),
    );
  }
}
```