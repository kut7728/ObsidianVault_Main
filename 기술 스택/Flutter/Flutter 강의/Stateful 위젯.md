---
상위 항목:
  - "[[인프런 강의]]"
---
## 왜 생겼는가?

- 위젯은 불변의 법칙을 따른다  
    → 이미 생성된 위젯은 삭제하고 변경하여 새로 그려야함  
    → build() 함수를 재실행하여 새로 그림 - Hot Reload는 개발 할때만 가능  
    

  

## 무엇이 다른가?

- 클라스 선언이 한번으로 끝나는 Stateless와 달리 두개 선언
    
    ```Dart
    class HomeScreen extends StatefulWidget{
    
    	@override
    	State<HomeScreen> createState() => _HomeScreenState();
    }
    
    class _HomeScreenState extends State<HomeScreen>
    ```
    
- setState() 함수를 실행 함으로서 build() 함수를 재실행 시킬 수 있음

  

## 실습

- 코드
    
    ```Dart
    import 'package:flutter/material.dart';
    
    class HomeScreen extends StatefulWidget {
      const HomeScreen({super.key});
    
      @override
      State<HomeScreen> createState() => _HomeScreenState();
    }
    
    class _HomeScreenState extends State<HomeScreen> {
      Color color = Colors.red;
    
      @override
      Widget build(BuildContext context) {
        return Scaffold(
          body: Center(
            child: Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: [
                FloatingActionButton(
                  child: Text('색상 변경'),
                  onPressed: () {
                    if (color == Colors.red) {
                      color = Colors.blue;
                    } else {
                      color = Colors.red;
                    }
                    print('색상변경 : $color');
                    setState(() {
    
                    });
                  },
                ),
                SizedBox(
                  width: 30,
                  height: 30,
                ),
                Container(
                  width: 50,
                  height: 50,
                  color: color,
                ),
              ],
            ),
          ),
        );
      }
    }
    ```